<p align="center">
    <img width="200px;" src="https://raw.githubusercontent.com/woowacourse/atdd-subway-admin-frontend/master/images/main_logo.png"/>
</p>
<p align="center">
  <img alt="npm" src="https://img.shields.io/badge/npm-%3E%3D%205.5.0-blue">
  <img alt="node" src="https://img.shields.io/badge/node-%3E%3D%209.3.0-blue">
  <a href="https://edu.nextstep.camp/c/R89PYi5H" alt="nextstep atdd">
    <img alt="Website" src="https://img.shields.io/website?url=https%3A%2F%2Fedu.nextstep.camp%2Fc%2FR89PYi5H">
  </a>
  <img alt="GitHub" src="https://img.shields.io/github/license/next-step/atdd-subway-service">
</p>

<br>

# 인프라공방 샘플 서비스 - 지하철 노선도

<br>

## 🚀 Getting Started

### Install
#### npm 설치
```
cd frontend
npm install
```
> `frontend` 디렉토리에서 수행해야 합니다.

### Usage
#### webpack server 구동
```
npm run dev
```
#### application 구동
```
./gradlew clean build
```
<br>


### 1단계 - 웹 성능 테스트
1. 웹 성능예산은 어느정도가 적당하다고 생각하시나요

2. 웹 성능예산을 바탕으로 현재 지하철 노선도 서비스의 서버 목표 응답시간 가설을 세워보세요.


---

### 2단계 - 부하 테스트 
1. 부하테스트 전제조건은 어느정도로 설정하셨나요
   - 대상 시스템 범위 : WEB(ngnix), WAS(tomcat), DB(MySQL)

   - 목표값 설정
     - DAU(1일 사용자 수)
       - 지하철 한달 평균 승객 수 125982860
       - 하루 사용자 수 = 한달 평균 승객 수 / 30 = 4,199,420
       - 420,000 = 하루 사용자 수 중 10% 사용자만 사용한다고 가정

   - 피크 시간대의 예상 집중률
     - 2배 정도로 설정하였습니다.(https://www.bigdata-map.kr/datastory/traffic/seoul)

   - 1명당 1일 평균 예상 접속 혹은 요청수
     - 2번으로 설정하였습니다.(https://news.mt.co.kr/mtview.php?no=2021090916014079809)

   - Throughput
     - 1일 총 접속 수 = DAU X 1명당 1일 평균 접속수 = 840000
     - 1일 평균 rps = 1일 총 접속 수 / 86,400 (초/일) = 840000/86,400 = 9.7
     - 1일 최대 rps = 1일 평균 rps X (최대 트래픽 / 평소 트래픽) = 19.4

   - VUser
     - T = 4 * 0.1 (+1s) = 1.4
     - VUser(평균) = (9.7 X 1.4) / 4 = 3.39
     - VUser(최대) = (19.4 X 1.4) / 4 = 6.79

   - latency
     - 100ms

2. Smoke, Load, Stress 테스트 스크립트와 결과를 공유해주세요

---

### 3단계 - 로깅, 모니터링
1. 각 서버내 로깅 경로를 알려주세요

2. Cloudwatch 대시보드 URL을 알려주세요
