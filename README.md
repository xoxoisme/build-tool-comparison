# build-tool-comparison
Maven과 Gradle 특징을 기록합니다.

---

## 요약

|      항목       |      Maven      |       Gradle        |
| :-------------: | :-------------: | :-----------------: |
|    설정 방식    |       XML       | Groovy / Kotlin DSL |
|    설정 파일    |     pom.xml     |    build.gradle     |
|    빌드 속도    | 상대적으로 느림 |        빠름         |
|     유연성      |      낮음       |        높음         |
|   학습 난이도   |      쉬움       |   상대적으로 높음   |
| 프로젝트 표준화 |      강함       |      자유로움       |

---

## Maven

### `pom.xml` 파일을 사용해 프로젝트를 설정한다.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

- 구조가 명확하나 **장황한 편**이다.

### 표준화된 프로젝트 구조를 사용한다.

```bash
project
 ├ src
 │  ├ main
 │  │  ├ java
 │  │  └ resources
 │  └ test
 │     └ java
 └ pom.xml
```

- **구조가 항상 동일**하고, 협업 시 이해하기 쉽다는 장점이 있다.

### Lifecycle 기반으로 동작한다.

```
유효성 검사(validate)
↓
컴파일(compile)
↓
단위 테스트(test)
↓
패키징(package)
↓
검증(verity)
↓
인스톨(install)
↓
배포(deploy)
```

### 오래된 도구라 안정성과 성숙도를 장점이라 말할 수 있다.

## Gradle

### `build.gradle` 파일을 사용해 프로젝트를 설정한다.

```gradle
dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
}
```

- `XML`보다 간결하고 **가독성이 좋다**.

### 빌드 속도가 빠르다.

- **Incremental Build**(변경된 코드만 따로 빌드) 특징을 가지고 있다. Maven은 다시 처음부터 빌드해야 하는 번거로움이 있다.
- 이전에 빌드한 결과를 **캐시**해서 재사용한다.
- 여러 Task를 병렬 실행할 수 있다.

### 코드 기반이라 조건문, 반복문을 사용할 수 있다.

- 각 모듈마다 반복하거나 조건문을 써 자유로운 방식으로 사용가능하다는 장점이 있다.

