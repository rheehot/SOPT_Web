## ✔️ React Notion App 만들기

`$ npx create-react-app 4th-seminar-react-project`

## ✔️ 불필요한 아이콘, 코드 삭제 및 변경

## ✔️ scss 세팅 및 적용

#### 🐝 sass 라이브러리 다운

` $ yarn add node-sass@4.14.1`

#### 🐝 scss 파일 생성 및 import

📃 App.scss

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@200;400;600&display=swap');

* {
  box-sizing: border-box;
}

.App {
  min-width: 600px;
}
...
```

📃 App.js

```js
import './App.scss';
```

## ✔️ react-router-dom을 이용한 전체 Component 구성하기

## & 중첩 라우팅을 이용해 MemberList, MemberDetail 분리

#### 🐝 react-router-dom 라이브러리 다운

` $ yarn add react-router-dom`

#### 🐝 컴포넌트 구조 설계 및 구조짜기

<img src="https://user-images.githubusercontent.com/22907830/98641951-f4c7aa00-236f-11eb-9ece-bc307f70ada6.png" alt="drawing" width="600"/>

```
#  폴더구조
src
  App.js
  ㄴcomponents
    ㄴheader
      ㄴHeader.js
  ㄴpages
    ㄴmain
      ㄴMain.js
    ㄴmember
      ㄴMemberList.js
      ㄴMemberDetail.js
```

📃 App.js

```js
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import Main from './pages/main/Main';
import Member from './pages/member/Member';
import MainHeader from './components/header/MainHeader';

function App() {
  return (
    <Router>
      <div className="App">
        <MainHeader /> {/* global navigation bar */}
        <Switch>
          {/* exact : path에 따라 맞는 컴포넌트 출력 */}
          <Route exact path="/" component={Main} /> {/* 메인 화면 */}
          <Route path="/member" component={Member} /> {/* 멤버 리스트 출력 */}
          <Route path="*">
            {/* 404 페이지 */}
            <h1> 404 NOT FOUND </h1>
          </Route>
        </Switch>
      </div>
    </Router>
  );
}
```

📃 MainHeader.js

```js
function MainHeader() {
  return <header>여기는 header입니다</header>;
}

export default MainHeader;
```

📃 Main.js

```js
function Main() {
  return <h1> 메인 페이지 </h1>;
}

export default Main;
```

📃 Member.js

```js
import { Switch, Route } from 'react-router-dom';
import MemberList from './MemberList';
import MemberDetail from './MemberDetail';

function Member({ match }) {
  // match : { params, url, path ... }
  // match.path : '/member'
  return (
    <section>
      <Switch>
        {/* exact path는 정확히 라우트가 맞아떨어져야만 컴포넌트 select */}
        <Route exact path={match.path} component={MemberList} />
        <Route path={`${match.path}/:id`} component={MemberDetail} />
      </Switch>
    </section>
  );
}

export default Member;
```

📃 MemberList.js

```js
function MemberList() {
  return <h1>MemberList Page</h1>;
}

export default MemberList;
```

📃 MemberDetail.js

```js
function MemberDetail() {
  return <h1>MemberDetail Page</h1>;
}

export default MemberDetail;
```

## ✔️ MainHeader 만들기

#### 🐝 history push를 위해 route 컴포넌트로 변경

📃 App.js

```js
  ...
  <div className="App">
    {/* global navigation bar */}
    <Route component={MainHeader} />
    <Switch>
    ...
```

#### 🐝 antd, antd/icons 다운

`$ yarn add antd`

`$ yarn add @ant-design/icons`

#### 🐝 Button component 생성

📃 Button.js

```js
import './Button.scss';

function Button({ text, textColor = '#444', onClickFunc }) {
  return (
    <span className="button" style={{ color: textColor }} onClick={onClickFunc}>
      {text}
    </span>
  );
}

export default Button;
```

📃 Button.scss

```css
.button {
  border-radius: 4px;
  padding: 4px 8px;
  &:hover {
    background: #eee;
    cursor: pointer;
  }
  &:active {
    background: #ccc;
  }
}
```

#### 🐝 header component 작성

📃 MainHeader.js

```js
import './MainHeader.scss';
import { MenuOutlined } from '@ant-design/icons';
import Button from '../button/Button';

function MainHeader({ history }) {
  // history : { go, goBack, goForward, location, push ...}
  return (
    <header className="main-header">
      <nav className="main-header__nav" id="left-gnb">
        <MenuOutlined type="icon" className="main-header-icon" />
        <Button
          text="[ON SOPT] Web Part"
          onClickFunc={() => history.push('/')}
        ></Button>
        <span>&nbsp;/&nbsp;</span>
        <Button
          text="파트원 소개"
          onClickFunc={() => history.push('/member')}
        ></Button>
      </nav>
      <nav className="main-header__nav" id="right-gnb">
        <Button text="Share"></Button>
        <Button text="Updates"></Button>
        <Button text="Favorites"></Button>
        <Button text="…"></Button>
      </nav>
    </header>
  );
}

export default MainHeader;
```

📃 MainHeader.scss

```css
.main-header {
  display: flex;
  height: 45px;
  padding: 12px;
  font-size: 14px;
  justify-content: space-between;
  .empty {
    flex: 1;
  }
  &-icon {
    height: 100%;
    margin-right: 12px;
    cursor: pointer;
  }
}
```

## MemberList & Card Component 구현

📃 .js

```js

```

## Loading Component 구현

📃 .js

```js

```

## MemberDetail Component 구현

📃 .js

```js

```
