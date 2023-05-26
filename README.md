# 프리미엄 식품관 런칭을 위한 데이터 분석

- 멋쟁이사자처럼 AI SCHOOL 8기 데이터톤
- Member: 멋쟁이사자처럼 AI SCHOOL 8기 1조
- Status: Complete
- Period: 23.05.10 ~ 23.05.19

![스크린샷 2023-05-20 오후 11 36 20](https://github.com/seoinhyeok96/Datathon/assets/125840482/22a7c2b9-89ea-48f5-9571-fe54d9865a19)


## 1. 타겟 및 상황 설정
<p align="left"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/3961fb0b-c174-45a9-b922-c0089cec976c" weight=600 height=300/></p>

캐릭터 출처 : 망그러진 곰(@yurang_official)

> **이름** : 곰잘레스
> 
> 
> **직무** : MD(Merchandiser)
> 
> **연차** : 3개월
> 
> **특징** : MD하려고 에콰도르 옴
> 
> **임무** : 프리미엄 식품관 런칭 프로모션을 기획하라!
> 


**문제 상황**

Quito 지역 매장은 주로 **고소득층 고객**이 많다.

따라서 올해 Quito 지역 스토어에 **프리미엄 식품관 런칭**할 계획이다.

런칭 기념으로 올해 **축제 기간을 활용한 프로모션**을 준비하고자 한다.

이 프로모션의 목표는 프리미엄 식품관의 인지도를 높이고 축제 분위기와 더불어 식품관에 대한 긍정적인 이미지를 만드는 것이다.

이제 프로모션을 진행할 축제는 어떤 축제로 할지, 어떤 품목을 전면적으로 내세울지, Quito지역 18개 스토어 중 프로모션 효과가 가장 클 곳은 어디일지 정해야한다.

## 2. 데이터 소개
- Kaggle의 Store Sales - Time Series Forecasting 데이터셋
- 에콰도르 Favorita 마트에서 판매되는 여러 제품군에 대한 2013 ~ 2017년 매출 데이터

| data | shape | description |
| --- | --- | --- |
| train | (3000888, 6) | 날짜, 매장 번호, 제품의 카테고리, 프로모션 개수 및 판매량  |
| test | (28512, 5) | 날짜, 매장 번호, 제품의 카테고리 및 프로모션 개수 |
| holidays_events | (350, 6) | 날짜, 휴일 종류, 지역 크기, 지역 이름 및 공휴일명 |
| oil | (1218, 2) | 날짜 및 일일 유가 |
| stores  | (54, 5) | 매장 번호, 도시, 주, 매장 유형 및 매장 클러스터 번호 |
| transactions | (83488, 3) | 날짜, 매장 번호 및 거래량 |

## 3. 분석 과정

## **3.1. EDA**

### 1. 프로모션 기간 선정

**Q. 키토 지역에서 가장 판매량이 높은 축제(공휴일)는 언제였나요?**

1) **연도별 국가 행사 및 키토 지역 행사 판매량(sales) 목록**

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/17bce4ec-b7eb-4673-9503-10f05c0f1bc7" weight=800 height=400/></p>

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/1e5028c9-2993-4f21-a639-643ac15f98c3" weight=800 height=400/></p>

⇒ 연도별 국가 행사 및 키토 지역 행사 판매량을 비교한 결과 **매년 공통적으로 크리스마스 시기에 높은 판매량을 기록**

2) **연도별 크리스마스 기간 판매량(sales) 추이**

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/44fdb7cd-baf5-492f-a6ae-c979f80b5894" weight=600 height=300/></p>

⇒ **매년 크리스마스 기간** 판매량(sales)이 증가하는 추세

**Q. 그렇다면 적절한 프로모션 시작 일자 및 기간은 언제가 좋을까요?**

1) **크리스마스 전후 7일간 판매량(sales) 변화**

<p align="center"><img src="https://github.com/haLinnn/Datathon/assets/108817458/47dd13dc-a3cc-4fe1-9eba-eec27894c3ea" weight=450 height=450/></p>

⇒ **12월 18~20일**부터 크리스마스 준비로 인해 판매량(sales)이 눈에 띄게 증가함

2) **크리스마스 전후 한 달간 판매량(sales) 변화**

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/dbf0f5a4-7b83-479f-82db-782589d6f8f9" weight=450 height=450/></p>

⇒ **크리스마스 한 달 전**부터 꾸준히 판매량(sales) 상승세

⇒ **11월 말부터 매체 홍보 시작, 12월 중순부터 오프라인 프리미엄 식품관 오픈 권장**


`💡 결론`

> Q. 키토 지역에서 가장 판매량이 높은 축제(공휴일)
>   
> A. 크리스마스
> 
> Q. 적절한 프로모션 시작 일자 및 기간
>  
> A. 매체 홍보 : 11월 말부터 시작, 오프라인 식품관 프로모션 시작 : 12월 중순 ~ 12월 24일



### 2. 프로모션 품목 선정

**Q. 크리스마스에 주로 잘 팔리는 제품은 무엇이었나요?**

1) 키토 지역 내 스토어에서 FROZEN FOODS의 판매량(sales) 현황
:  **FROZEN FOODS(냉동 식품)** 은 연말마다 판매량(sales)이 폭발적으로 증가

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/10739774-14e5-4de9-8c3e-ac0b40562961" weight=800 height=400/></p>


2) 키토 지역 내 스토어에서 LIQUOR, WINE, BEER의 판매량(sales) 현황
:  **LIQUOR, WINE, BEER(주류)** 도 연말마다 판매량(sales)이 증가

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/9ffb1f5d-b953-400a-929e-d853abae5481" weight=800 height=400/></p>


3) **키토 지역의 품목별 판매량(sales) 비교** (모든 월 vs. 크리스마스 기간)

- 모든 월과 크리스마스 기간 모두 판매량(sales)이 높은 품목은 대부분 **식품**(GROCERY 1, PRODUCE, BEVERAGES, DAIRY, MEATS, BREAD/BAKERY, DELI)
- 특히 모든 월 대비 크리스마스 기간에 잘 팔리는 품목은 **FROZEN FOODS(냉동식품)**


<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/14ec7922-61e5-4a34-91e3-790fd1ebb444" weight=600 height=300/></p>


<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/be592ccb-fb42-4f1b-850a-65ae774b184c" weight=600 height=300/></p>


<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/d94307e7-654b-4a0b-acf5-2d631220a146" weight=600 height=300/></p>


<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/36d0a00d-4470-450c-87ca-285247c0b5f6" weight=600 height=300/></p>


⇒ 프리미엄 식품관 프로모션 시, **냉동식품**에 집중

⇒ 상품 기획 아이디어 : **고급 냉동 밀키트** (고급 레스토랑과 콜라보)


`💡 결론`

> Q. 키토 지역에서 크리스마스에 주로 잘 팔리는 품목
>   
> **A. GROCERY 1(식료품), FROZEN FOODS(냉동 식품), LIQUOR,WINE,BEER(주류)**
> 
> ⇒ 프리미엄 식품관 프로모션 시, **냉동식품**에 집중
> 
> ⇒ 상품 기획 아이디어 : **고급 냉동 밀키트** (고급 레스토랑과 콜라보)



### 3. 프로모션 스토어 선정

**Q. Quito 지역 스토어 중 가장 판매량(sales)이 높은 스토어는 어디인가요?**

A.  **44번 매장**

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/a2471f71-54e6-499f-811e-afd298a18080" weight=450 height=450/></p>


**Q. 최근 1년(2016년 한 해동안)간 판매량(sales)이 가장 많았던 스토어는 어디인가요?**

A.  **44번 매장**

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/06230d7b-eaf2-4dc3-bd7c-5c6e689dae89" weight=450 height=450/></p>


**Q. Quito 지역 스토어 중 가장 거래 건수가 많은 스토어는 어디인가요?**

A.  **44번 매장**

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/6fc43f6c-6b3b-467a-b9ab-b9610e50e0d1" weight=450 height=450/></p>


**Q. 최근 1년(2016년 한 해동안)간 거래량(거래건수)이 가장 많았던 스토어는 어디인가요?**

A.  **44번 매장**

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/33f433b9-9cab-43a4-9a3f-6fa82fba6c5e" weight=450 height=450/></p>


**Q. (전체 기간 기준) 거래건수 대비 판매량이 높게 나오는 스토어는 어디인가요?**

A. 기존 판매량 & 거래건수에서 상위였던 매장들이 상위에 존재

   ⇒ 거래건수에 대비해서 판매량이 가장 많았던 매장은 **3번 매장**

   ⇒ 즉, 3번은 한번에 많은 물건을 주로 구매하는 큰 손 고객이 많은 스토어
   
<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/3f4072d6-692b-4ab1-b233-6c3b84659951" weight=450 height=450/></p>



**Q. 지금까지 프로모션 효과가 좋았던 스토어는 어디인가요?**

⇒ 프로모션 횟수와 판매량(sales)은 양의 선형관계가 있음.

⇒ 40번대 스토어가 지금까지 프로모션을 많이 진행했으며 평균 판매량(sales)도 높게 나옴.

⇒ 특히 3번 스토어는 40번대 스토어들보다 프로모션은 적게 했지만 평균 판매량(sales)이 꽤 잘 나왔음.

⇒ 지금까지 프로모션을 많이 진행해 인지도가 높은 **47번, 44번** 스토어

⇒ 프로모션 효율이 좋은 **3번** 스토어

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/95c364ca-313c-446f-bc41-fbef9a25f86c" weight=600 height=300/></p>


`💡 요약`

> Q. Quito 지역 판매량(sales) 상위 스토어
> 
> A. **44**, 45, 47, 3, 49 순
> 
> Q. 최근 1년(2016년 한 해동안)간 판매량(sales)이 가장 많았던 스토어
> 
> A. **44**번 스토어가 모든 기간 1위 (참고. 16년 10월부터 47번이 3번의 판매량을 추월)
> 
> Q. Quito 지역 거래건수(transactions) 상위 스토어
> 
> A. **44**, 47, 45, 46, 3 순
> 
> Q. 최근 1년(2016년 한 해동안)간 거래량(거래건수)이 가장 많았던 스토어
> 
> A. **44**번 스토어가 모든 기간 1위
> 
> Q. 거래건수 대비 판매량 상위 스토어
> 
> A. 3, 49, 7, 45, 44 순


`💡 결론`

> **스토어(44번)만의 특징**
> 
> - 판매량, 거래건수 모두 압도적 1위
> - 프로모션 다수 진행으로 높은 인지도 보유
> 
> ⇒ Sales(판매량) & Transactions(거래건수)이 모두 상위인 **44번 스토어**를 추천


## 3.2. 머신러닝을 통한 판매량 예측

- 예측 시기 : 2017년 12월 1일 ~ 12월 24일
- 예측 항목 : 44번 스토어의 FROZEN FOOD(냉동 식품)의 프로모션 수에 따른 sales
- 예측 순서 : 프로모션 개수 설정 → sales 예측
- 사용 데이터 : train_quito, holidays_events, test_quito
- 모델 선정 : AutoML → 상위 성능 모델 선정 → 하이퍼파라미터 튜닝을 통한 성능 향상

### 1. 프로모션 개수 설정

- **Frozen Foods**
    
    <p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/facb21a4-ef30-4279-88c7-282f1894b8d1" weight=600 height=300/></p>
    
- 평균 프로모션 수
    - 2014년 평균 프로모션 수 : 4
    
    <p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/75aef5fe-71b1-4794-b66a-2d02999e562b" weight=600 height=300/></p>
    

    - 2015년 평균 프로모션 수 : 2
    
    <p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/8be670b7-955e-4513-bc6d-8acb41ef8a70" weight=600 height=300/></p>

    
    - 2016년 평균 프로모션 수 : 5

    <p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/004d0457-8a73-4302-8cad-ff08d5977d43" weight=600 height=300/></p>
    
    
    예측 결과를 토대로 프로모션 개수를 다르게 설정
    
    - test 1 : 2주전 프로모션 개수 10번/15번으로 증가 (11일~ 24일)
    - test 2 : 1주전 프로모션 개수 10번/15번으로 증가 (18일~ 24일)
    
    데이터셋 생성 후 2017년 12월 Frozen Food의 판매량을 예측
    
    → 가장 판매량이 높게 나온 test set을 프로모션 기획에 활용
    

### 2. 데이터 전처리

- 피처 선정
    - 품목분류 == 'FROZEN FOODS'(냉동식품)
    - 매장번호 == 44
    - 필요 컬럼 : '`날짜`', '`판매량`, '`프로모션진행개수`'
- holiday 데이터셋 결합
    - 휴일 유무 반영 위해 holiday 데이터셋을 test 데이터셋에 결합
    - 휴일 유무 one-hot-encoding
    
    <p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/ea7bb456-50be-41e9-9fd0-31b43ce2c1bd" weight=400 height=200/></p>

- 파생변수 생성
    - '날짜'컬럼 datetime 형식으로 변경
    - ‘`년`’, ‘`월`’, ‘`일`’, '`요일`'파생변수 생성
    

### 3. 모델 선정

- Auto ML을 통해 상위 3가지 모델을 선정
    - LGBM
    - RandomForest
    - XGBoost

### 4. 하이퍼파라미터 튜닝

하이퍼파라미터 최적화 라이브러리 `optuna` 를 통한 튜닝

### 5. 예측 결과

- 예측 성능 확인 그래프
    - r2 score: 0.915
        
        <p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/4811d077-ef7f-454f-adef-df98f071a0bd" weight=450 height=450/></p>
        
- 1주 전 vs 2주 전

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/c83420ba-7ab4-4604-981f-4b74497d173c" weight=600 height=300/></p>


> 📍 2주 전 진행하는 것이 판매량이 소폭이지만 상승 (약 12%)
>
> 따라서 프로모션 진행 지출 비용을 고려하여 진행기간을 선정하는 것이 필요


- 프로모션 개수 : 10개 vs. 15개
    - 프로모션 비용을 고려하여 프로모션 개수를 다량으로 늘리지 않음

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/db959c72-d5c3-4ccd-89eb-147b2d18f8d5" weight=600 height=300/></p>

> 📍 프로모션 10, 15개의 차이가 없음 → **기회비용을 고려하여 10개를** 권장


## 4. 분석 결과

<p align="center"><img src="https://github.com/haLinnn/LIKELION_AI_SCHOOL_DATATHON/assets/108817458/64ee92e2-cb5d-40eb-9b8c-90145011efd5" weight=450 height=450/></p>
