## POST css

- 컴포넌트 별로(모듈) css를 만들어 사용할 수 있다.

```css
<!--
  -------------------------
  Button1.module.css
  --------------------------
  --
  > .button {
  background-color: 'aqua';
}
```

```js
<!-- ----------------------------- Button1.jsx ----------------------------- -->
import styles from './Button1.module.css'

function Button1(){
  return <button className={styles.button}>Button</button>

}

```

- 브라우저 결과:
- class="Button1_button_S9YbLe"
- 파일이름\_클래스이름\_id

## Styled Components

- 자바스크립트 파일내에서 스타일을 만들어 사용
- yarn add styled-compoents

```js
import styled, { css } from 'styled-compoents';

const Container = styled.div`
  display: 'flex';
`;

const Button = styled.button`
  background: transparent;
  border-radius: 3px;
  border: 2px solid #3c5b69;
  color: #b9eaff;
  margin: 0 1em;
  padding: 0.25em 1em;
  ${(props) =>
    props.primary &&
    css`
      background: #009cd5;
      color: white;
    `};
`;

export default function StyleComponent() {
  // 자바스크립트 내에서 스타일을 만들어 사용하는 특징이 있다.
  // 그러나 3개이상만 만들어도 너무 복잡할 거 같아서 사용하고 싶지 않다.
  return (
    <Container>
      <Button>Normal Button</Button>
      <Button primary>Primary Button</Button>
    </Container>
  );
}
```

## tailwind

- 팀프로젝트 떄 사용 해봤는데 바닐라 자바스크립트에서는 class가 너무 많아지는 거 같아 선호하지 않았었는데
- 리액트는 JSX문법을 사용하기 떄문에 괜찮다는 생각이 들었다.(좀 더 사용해봐야 할듯하다.)
- 설치 방법은 생략한다.(공식문서 참고)

## 장단점 비교

- Post Css:

  - 성능: pure Css
  - 활용성: 어디서든 사용가능
  - 강점: 고립성/독립성, 순수 CSS -> 입문자에게 제일 좋음

- Styled Components:

  - 성능: Css in Js
  - 단점: 성능에 좋지 않음, 재컴파일 되어야 함
  - 활용성: React, React-Native에서만 사용가능
  - 강점: 고립성/독립성, JavaScript를 통한 편의성
    - 비지니스 로직과 스타일이 뒤엉킴

- Tailwind:
  - 성능: pure Css -> 미리 정해진 클래스 이름들을 조립
  - 단점: 사용법을 익혀야함
  - 활용성: 어디서든 사용가능
  - 강점: 잘 정의된 디자인 시스템, 클래스 이름 창작의 괴로움이 적다. 태그와 스타일을 함께!
    - 다소 난잡해 보일 수 있다.(유지보수하기 어렵지만 편한방법이 있다.)
