# Zipkin Test 를 위한 레파지토리입니다. 

실행흐름

- Eureka Server > Order > Product 순으로 실행합니다.
- http://localhost:19091/order/1 를 접속해봅니다. 이전의 응답과 결과가 같습니다.
    - 일반 브라우저에서 접속        
    - Talend 접속
              
- http://localhost:9411/zipkin/ 로 접속 후에 RUN QUERY를 클릭합니다. 리스트가 나오며 Spans 3 인 항목의 SHOW를 클릭합니다.    
- Order-service가 Product-service를 호출하는 과정이 트래킹 되는 것을 확인 할 수 있습니다.

---

## 분산 추적을 위해 Zipkin 사용

### Zipkin

- Zipkin은 트레이스 데이터를 수집하고 시각화하는 분산 추적 시스템입니다.
- 각 서비스의 트레이스와 스팬 데이터를 저장하고, 이를 통해 호출 흐름을 시각화합니다.

### - 주요 특징

- **데이터 수집 및 저장**: 각 서비스에서 전송된 트레이스 데이터를 수집하고 저장합니다.
- **시각화**: 트레이스 데이터를 시각화하여 서비스 간의 호출 관계를 명확히 파악할 수 있습니다.
- **검색 및 필터링**: 특정 트레이스나 스팬을 검색하고 필터링하여 문제를 진단할 수 있습니다.



## Zipkin 서버 설정


  ### 9.4.1 Zipkin 서버 실행
<details><summary>도커 사용하여 실행</summary>
- Zipkin 서버를 Docker를 사용하여 실행할 수 있습니다:
    
    ```bash
    docker run -d -p 9411:9411 openzipkin/zipkin
    ```
</details>

 <details><summary>Zipkin 대시보드 사용</summary>   

- Zipkin 대시보드에 접속하여 트레이스 데이터를 시각화합니다:
    - URL: `http://localhost:9411`
    - 트레이스 검색 및 분석
</details>
    
---

##  **분산 추적 예시**

### 1. 서비스 호출 흐름 추적

- 예제 서비스 간의 호출 흐름을 추적하고, Zipkin 대시보드에서 시각화합니다.
- 각 서비스 호출 시 트레이스와 스팬이 생성되고, Zipkin 서버로 전송됩니다.

### 2. 성능 병목 진단

- Zipkin 대시보드를 통해 성능 병목이 발생하는 부분을 식별합니다.
- 각 스팬의 소요 시간과 호출 관계를 분석하여 성능 문제를 진단하고 해결합니다.
