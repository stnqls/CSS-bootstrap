# Bootstrap 사용하기

## [bootstrap](https://getbootstrap.com/)

### 1. CSS연결하기
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
```
### 2. JS연결하기 <br/>
외부의 `Popper.js`의 패키지를 사용하고 있다. <br/>
`Popper.js`: 팝업을 좀더 쉽게 만들수 있는패키지이다. 

### 2-1. CDN으로 연결하기
- Bundle (프로젝트에서 popper를 사용하고 있지 않은경우)
```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
```
- Separate (프로젝트에서 popper를 사용하고 있는경우)
```html
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js" integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js" integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
```
### 2-2. NPM프로젝트로 실행하기
CDN으로 설치할경우 기능제한이 있다.<br/>
사용하는 기능만 따로 사용이가능하며, Customize가 가능하다.

```bash
$ npm init -y
$ npm i -D parcel-bundler
$ npm install bootstrap@next
```
- js에 연결하기
```js
import bootstrap from 'bootstrap/dist/js/bootstrap.bundle'
```
- scss에 연결하기
```scss
@import "../node_modules/bootstrap/scss/bootstrap";
```
### * Customize사용하기
1. 필수요소 가져오기
- scss
```scss
// Required
@import "../node_modules/bootstrap/scss/functions";

$theme-colors: (
  "primary":    pink,
  "secondary":  $secondary,
  "success":    $success,
  "info":       $info,
  "warning":    $warning,
  "danger":     $danger,
  "light":      $light,
  "dark":       $dark
);
// primary가 적용된 태그는 색상이 pink색상으로 변경된다.
```
### * Optimize (성능최적화)사용하기
- js에서 개별적으로 가지고오기
```js
//import bootstrap from 'bootstrap/dist/js/bootstrap.bundle'
import Dropdown from 'bootstrap/js/dist/dropdown'

//초기화내용이 필요하다.
const dropdownElementList = [].slice.call(document.querySelectorAll('.dropdown-toggle'))
dropdownElementList.map(function (dropdownToggleEl) {
  return new Dropdown(dropdownToggleEl)
})
```
초기화가 필요한 컴포넌트가 있고, 필요없는 경우가 있다.<br/>
개별적으로 사용할경우 `Popper.js`패키지를 따로 설치해주어야 한다.
```bash
$ npm i @popperjs/core
```

### 3. Components를 선택해서 사용하기
