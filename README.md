# 2023_maicon
![Untitled](https://github.com/ssongm2/2023_maicon/assets/157574142/a92d0d91-6332-4e7d-bba8-e6b140fc43dd)

## 프로그램 소개

프로그램명: 2023 국방 AI 경진대회 <일반인 부문>

주최: 국방부, 과학기술정보통신부

기간: 2023.11.29 ~ 2023.12.01

## 개발 과정

**주제: 딥페이크 비디오 판별 모델 개발**

1. 문제 이해
    - Deepfake detection 모델은 가짜 영상의 생성 과정에서 발생하는 부자연스러움, 해상도 불일치, 고주파 성분 재현력 등의 특징을 찾을 수 있도록 학습
    - 입력 영상의 binary classifcation, 즉 real과 fake를 구분하는 것으로 VGG, ResNet 등의 Image Classification에 쓰이는 다양한 신경망 사용
2. 데이터 활용
    1) 프레임 추출
        - 모든 프레임 추출
    2) 전처리
        - Random Horizontal Flip
          데이터의 다양성을 위해 랜덤한 확률로 데이터 좌우 반전
        - Center crop
          모든 영상이 깨끗한 배경 가운데에 사람의 상반신이 나온 영상이므로 얼굴 부분을 자르기 위해 center crop
          얼굴을 따로 detection하는 모델을 사용해보았으나 center crop보다 성능이 좋지 않음
        - Normalize
          이미지의 각 RGB 채널에 대해 평균과 표준편차 지정하는 데이터 정규화 적용
          채널이 비슷한 범위 내에 있도록 지정하여 모델 학습 안정화 시킴
3. 모델
    - ResNet을 적용했을 때 성능이 향상됨을 확인하고 베이스라인으로 지정, 이후 유사한 모델 적용하며 실험 진행
    - res2net50, resnext50d, resnest50d, inception_v4, xception
    - 기존에 성능이 좋았던 CNN 모델과 주파수 변환한 transformer model을 합쳐 새로운 모델 구축
    - xception + swinv2_transformer
    - 위 6개의 모델을 앙상블하여 소프트 보팅 진행
4. 성능
    - 정확도 0.982로 1위
5. 최종 합산 순위
    - 3위
