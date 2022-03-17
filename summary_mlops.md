# MLops summary
- 머신러닝을 연구하고 상용화하는 과정을 안정적이고 효율적으로 관리하기 위한 프로세스
   - 변성윤님의 깃헙을 기준으로 정리함
   - 

## 머신러닝 프로세스 - research단계와 product 단계 
- **research** :
   - 연구와 테스트 단계
   - 문제정의 - EDA - feature 생성 - 모델 학습 - 예측
   - 내 컴퓨터 또는 서버에서 실행하는 단계
   - 고정된 데이터를 사용함
- **product** :
   - 상용화 단계 : 머신러닝 모델을 실제 서비스화하는 과정
   - reserch 단계에서 만든 모델을 실제 서비스 환경에서 실행하면 많은 변수와 버그들이 발생함
   - input 데이터가 모델 구현 단계의 데이터와 동일한 범위인지, 다른지 등의 확인 필요
   - 새로 배포한 모델의 성능을 지속적으로 모니터링 해야함
   - research 단계에서 성능이 좋았던 모델이 product 단계에서 사용 못할 수도 있음
- **머신러닝 프로세스의 여러 분야**
   - configuration : 구성
   - data collection : 수집
   - feature extraction : 특징 추출
   - monitoring : 모니터링
   - data varification : 데이터 검증
   - machine resource management : 기계의 자원 관리
   - anlaysis tools : 분석 도구
   - process management tools : 과정 관리 툴
   - serving infrastructure : 서비스 인프라
   - monitoring : 모니터링 
   - ML coding : 머신러닝 코딩 (매우 작은 분야)
- 머신러닝 프로세스가 머신러닝 모델 개발과 머신러닝 모델 운영으로 나뉘게 된다.

## ML + Ops = MLOps
- `머신러닝 모델 개발과 운영 workflow의 간극을 줄이기 위해 생긴 분야`
- **model development / model prediction** 으로 세분화 됨
- **ml model development** :
   - training data ingestion : 트레이닝 데이터 수집(섭취)
   - data cleaning : 데이터 전처리
   - feature engineering : 여러 모델들을 만들고 특징 벡터들의 성능을 테스트함, 실험함, 
   - model selection / parameter search : 성능이 좋은 모델을 선택, 모델의 여러가지 파라메터들을 연구
   - persisted model : 지속할 수 있는 모델
- **ml prediction with trained model** : 훈련된 모델에 의한 예측 과정 (development의 persisted model의 성능 연구)
   - unseen data ingestion : 보이지 않는 데이터 수집(트레이닝 데이터에 포함되지 않았던 데이터)
   - data cleaning : 데이터 전처리
   - data transformation info features : 데이터 변환 정보 기능
   - model prediction : 모델 예측
   - result : 결론
- **즉 MLOps 는 머신러닝 모델을 서비스화하기 위한 세분 단위들의 연관성을 효율적으로 조정한 업무 프로세스의 의미**
- 머신러닝이 고도화 되고 서비스가 다변화 되면서 생기는 업무적 문제 상황들
- 실무적 차원에서 머신러닝 팀이 작은 경우
   - 소수의 모델 운영
   - 각자의 모델을 자신만의 방법으로 진행 상황추적, 성능 확인 가능
- 팀이 성자하면서 생기는 새로운 상황들
   - 데이터의 복잡도가 증가하기 시작함
   - 데이터 전처리 work flow가 길어짐
   - 데이터 전처리가 중앙에서 표준화 되지 않고 여기저기에서 갑자기 수정되는 일들 발생
   - 이러한 flow 를 관리하는게 어려워짐
- 사람마다 선호하는 프레임 워크가 다름
   - tensorflow, R, spark, keras, pytorch, MXnet 등... !!!! 나도 주특기인 프레임 워크를 가져야 할 거 같다.
- 모델을 배포하는 serving이 어려워진다.
   - 환경마다 실행이 달라지고, 라이브러리, 파이썬등의 버전에 민감해짐.
   - 모델을 배포한 후 성능이 좋지않을때 다시 과거 버전으로 롤백하는 과정도 복잡해질 수 있다.
- **이러한 복잡도들이 높아지면 결국 어디에서 오류, 버그 가 일어나는지 파악이 어려워지게 된다.**
   - 데이터 사이언티스트 들은 파이프라인의 문제라고 할 수 있고
   - 데이터 엔지니어들은 모델의 문제라고 할 수 있다. 

## MLOps의 목표
- `머신러닝 모델개발(ml dev)과 머신러닝 모델운영(Ops)에서 발생하는 문제들을 최소화하고, 비즈니스의 가치를 창출하기 위함`
   - 모델링에 집중할 수 있도록 안정된 인프라 구축, 운영을 자동화 함
   - research에서 production까지 최소시간으로 risk를 관리하면서 기술적 마찰을 줄이기 위함

## MLOps의 중요 원칙
- reproducibility : 재현성
   - research 단계에서 만든 모델이 production 환경에서도 재현되어야 한다. reproducibility
   - training data, tset data, real data가 유사한 분포를 가져야한다.
- orchestration : 오케스트레이션, 편성
   - 서비스의 자동화된 설정, 관리, 조정 등이 이루어져야 한다.
   - 예측에 대한 수요가 높아지면 내부 서버 증설 필요


## 데이터 직군들의 task : MLOps 관점에서
- data scientist : 모델 개발 ml dev
- data engineer : 파이프 라인 개발
- ml ops engineer : 모델, 파이프라인 및 production 부분 담당

## research ml과 production ml의 차이 
- research ml / production ml : 
   - 데이터 : 고정됨 / 계속해서 변한다 
   - 중요요소 : 모델의 성능 (accuracy, rmse) / 모델성능, 빠른 inference 속도, 해석 가능해야함
   - 도전과제 : 더 좋은 성능을 내는 모델, 새로운 구조의 모델개발 / 안정적인 운영, 전체 시스템 구조
   - 학습 : 모델구조, 파라미터 기반의 재학습 / 데이터가 변경됨로 모델을 재학습시킴
   - 목적 : 논문 출판 / 서비스에서 문제 해결
   - 표현 : offline / online

## MLOps component
- 요리하는 과정에 비유
   - **research** : 집에서 혼자 요리개발하는 과정
      - 집에서 맛있게 먹은 요리가 꼭 레스토랑에서 잘 팔리는 것은 아니다. 
      - 메뉴에 오르지 못할 수 도 있다.
   - **production** : 레스토랑에서 요리를 판매하는 환경
      - 재료 : data, feature
      - 음식 : 머신러닝모델
      - 요리하는 행위 : train
- **프로세스 세분화 비교**
   - Serving
   - Experiment, Model Management
   - Feature store
   - data validation
   - continuous training
   - monitoring
   - gpu infra management
   - auto ml

## Serving 
- 레스토랑에서 만든 음식을 손님에게 서빙하는 단계
- 머신러닝 모델도 소비자에게 서빙하는 것과 같다고 생각할 수 있다.
- Serving 에서 중요한 부분
   - 의존성 관리 : 라이브러리, 파이썬 버전, os 등
   - docker나 kubernetes를 많이 사용함
- **Serving 방식**
   - batch serving
   - online serving
   - edge serving (mobile)
- **Batch Serving**
   - 특정 시간에 서빙하는 개념, 가장 쉬운 방식
   - batch로 많은 양을 한꺼번에 처리하는 의미
   - 방식 : airflow나 cronjob 등으로 특정 시간에 학습하고 특정시간에 예측함 (1시간 단위, 1주일 단위 등)
   - 예측한 결과를 db table에 저장하고 서버에서 이값을 활용하는 방식으로 활용가능
- **online Serving**
   - API Serving, 주문하고 바로 음식을 만들어서 서빙하는 경우와 같다.
   - 음식을 한번에 하나씩 포장해서 배송해준다.
   - online 에서 실시간 request가 올경우 response로 반환함
   - 여러주문이 들어올 경우 확장 가능한 대응방안 필요하다. 여러 request가 들어올 경우
   - 진행해야 하는 예측이 batch 불가능한 경우
   - 실시간으로 빠르게 처리해야 하는 경우 사용하는 방식
   - flask / fastapi 를 사용해서 api 서버를 직접 개발하는 방식 사용 (docker 등에 올린다.)
   - serving 라이브러리 사용
      - kubeflow : 
      - bentoML : 간단한 사용 설명 참고하기
      - seldon core 
      - cortex
      - kfserving
      - tensorlow serving
      - torch serve
- 머신러닝 모델을 개발한 후 패키지화해서 Serving 을 한다. 
- 구글 클라우드의 practitioners guide to mlops 참고할만 함.

## Experiment, Model Management




















