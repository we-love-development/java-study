### 산술 연산자
- +, -, *, /, %
    - 넓은 자료형에서 좁은 자료형으로 형변환하는 것 주의! 값 손실이 일어날 수 있음
- ++, --
    - 후위 연산, 전위 연산 차이 잘 알아놓기
### 비트 연산자

  &, |, ^, ~,

  - 쉬프트 연산자 <<, >>, >>>
  - `>>` 는 오른쪽으로 이동하므로 부호를 주의해야 함
### 관계 연산자

  <, <=, >, >=, ==, !=

### 논리 연산자

  &&(AND), ||(OR), !(toggle)

### instanceof
- 객체의 타입 확인
- true, false 반환
### assignment(=) operator 대입 연산자
- 복합 대입 연산자
### 화살표(->) 연산자
- 람다식에서 사용되는 연산자 (Java 8부터)
- `(Parameter 매개 변수) -> {Body 함수 몸체}`

    ```java
    (int a, int b) -> {
      return a > b ? a : b;
    }
    
    (int a, int b) -> a > b ? a : b // 문장이 아닌 식인 경우 ; 붙이지 않음
    ```

### 3항 연산자
  코드가 간결해지더라도 컴파일 속도는 빨라지지 않는다고..

    result = (x > y) ? x : y;

### 연산자 우선 순위
1. 산술 > 비교 > 논리 > 대입. 대입은 제일 마지막에 수행됨
2. 단항 > 이항 > 삼항. 단항 연산자의 우선순위가 이항 연산자보다 높음
3. 단항 연산자와 대입 연산자를 제외한 모든 연산의 진행방향은 왼쪽에서 오른쪽
- (optional) Java 13. switch 연산자
    - 기존 코드

    ```java
    switch(test)
    {
        case 1:
            result = 3;
            break;
        case 2:
            result = 3;
            break;
        case 3:
            result = 33;
            break;
    }
    ```

    - Java 12

    ```java
    int test = 0;
    
    switch(test)
    {
        case 1, 2:
            result = 3;
            break;
        case 3:
            result = 33;
            break;
    }
    
    String result = switch(code) {
        case 1:
          break "code 1";
        case 2:
          break "code 2";
        default:
          break "default";
     };
    ```

    - break; 생략 가능

    ```java
    switch(test)
    {
        case 1, 2 -> 3;
        case 3 -> 33;
    }
    ```

    - Java 13

    ```java
    switch(test)
    {
        case 1, 2 -> 3;
        case 3 ->
        {
            yield 33;  // {} 블록 내부에서만
        }
        // case 3 -> yield 33; 블록 밖에서 쓸 수 없다.
    }
    
    String result = switch(code) {
    	  case 1:
    	    yield "code 1";
    	  case 2:
    	    yield "code 2";
    	  default:
    	    yield "default";
    };
    ```