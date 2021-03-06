##### 공부할 거리?
* 얼마나 많은 클라이언트와 서버가 통신하는지.
* 리소스(웹 콘텐츠)가 어디서 오는지
* 웹 트랜젝션이 어떻게 동작하는지
* HTTP 통신을 위해 사용하는 메시지의 형식
* HTTP 기저의 TCP 네트워크 전송
* 여러 종류의 HTTP 프로토콜
* 인터네 곳곳에 설치된 다양한 HTTP 구성 요소


## 1.1 HTTP: 인터넷의 멀티미디어 배달부

HTTP는 신뢰성 있는 데이터 전송 프로토콜을 사용한다.

=> 데이터의 왜곡, 손실, 중복 등을 걱정 안해도 된다. 개발자는 데이터 걱정 없이 기능 구현에 집중할 수 있음

## 1.2 웹 클라이언트와 서버

웹 서버는 HTTP 프로토콜로 의사소통하기 때문에 보통 HTTP 서버라고 불린다. 

웹 서버는 인터넷의 데이터를 저장하고 HTTP 클라이언트가 요청한 데이터를 제공한다.

## 1.3 리소스

웹 서버는 웹 리소스르 관리하기 제공한다. 웹 리소스는 웹 콘텐츠의 원천이다. 

리소스느 반드시 정적일 필요는 없다. 요청에 따라 콘텐츠르 생산하는 프로그램이 될 수도 있다.

즉 어떤 종류의 콘텐츠 소스도 리소스가 될 수 있다. ex) file, 웹 게이트웨이, 인터넷 검색엔진

### 1.3.1 미디어 타입 

HTTP는 웹에서 전송되는 객체 각각에 MIME 타입이라는 데잍 포맷 라벨을 붙인다. 

기존에는 이메일에서 사용 했으나, HTTP에서도 멀티미디어 콘텐츠를 기술하고 라벨을 붙이기 위해 채택되었다

MIME 타입은 사선(/)으로 구분된 주 타입(primary object type)과 부 타입(specific subtype)으로 이루어진 문자열 라벨이다.

* HTML로 작성된 텍스트 문서는 text/html 라벨이 붙는다.
* plain ASCII 텍스트 문서는 text/plain 라벨이 붙는다.
* JPEC 이미지는 image/jpeg가 붙는다.
* GIF 이미지는 image/gif가 된다. 

### 1.3.2 URI

웹 서버 리소스는 각자 이름을 갖고 있기 때문에 클라이언트는 관심 있는 리소스를 지목할 수 있다.

서버 리소스 이름은 통합 자원 식별자, 혹은 URI로 불린다.

URI가 해석되는 방법 : 
http://www.test.com/specials/saw-blade.gif

http:// -> http 프로토콜을 사용해라
www.test.com -> www.test.com으로 이동해라
/specials/saw-blade.gif -> /specials/saw-blade.gif라고 불리는 리소스를 가져와라.

### 1.3.3 URL

URL은 특정 서버의 한 리소승 대한 구체적인 위치를 서술한다. 정확하고 분명함

URL은 세부분으로 이루어진 표준 포멧을 따른다.
* URL의 첫 번째 부분은 스킴(scheme)이라고 불리는데, 리소스에 접근하 위해 사용되는 프로토콜을 서술한다.
* 두 번째 부분은 서버의 인터넷 주소르 제공한다.
* 마지막은 웹 서버의 리소스를 가리킨다.

### 1.3.4 URN(Uniform Resource Name)

URN은 콘텐츠를 이루는 리소스의 위치에 영향을 받지 않는 유일무이한 이름 역할을 한다. 

리소스 위치가 변해도 문제 없다. URN은 아직 많이 사용되지는 않는다.

## 1.4 트랜잭션

HTTP 트랜잭션은 요청 명령(클라이언트->서버)과 응답 명령(서버->클라이언트) 로 구성되어 있다. 

### 1.4.1 메서드

메서드 : 요청 명령 

모든 HTTP 요청 메시지는 한 개의 메서드를 갖는다. 메서드는 서버에 어떤 동작이 취해저야 하는지 말해준다. 

### 1.4.2 상태코드

### 1.4.3 웹페이지는 여러 객체로 이루어질 수 있다.

애플리케이션은 보통 하나의 작업을 수행하기 위해 여러 HTTP 트랜잭션을 수행한다.

ex) HTML 뼈대를 한번의 트랜젝션으로 가져온 후, 이미지, js 파일을 가져오기 위해 추가 HTTP트랜젝션들을 수행한다.

이와 같이 '웹페이지'는 보통 하나의 리소스가 아닌 리소스의 모음이다.

## 1.5 메시지

HTTP 요청과 응답 메시지의 구조
* 시작줄
** 시작줄로 요청이라면 무엇을 해야 하는지(메서드), 응답이라면 무슨일ㅇ이 일어났는지(상태코드)를 나타낸다.
* 헤더
** 각 헤더 필드는 쌍점(:)으로 구분되어 있는 하나의 이름과 값으로 구성
* 본문
** 임의의 이진 데이터 포함 가능
** 요청 : 웹서버로 데이터 전송
** 응답 : 클라이언트로 데이터 반환


## 1.6 TCP 커넥션

어떻게 TCP 커넥션을 통해 하 곳에서 다른 곳으로 옮겨가는지

### 1.6.1 TCP/IP

