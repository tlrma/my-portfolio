<div align="center">

# 황시은 Portfolio

<!-- 아래 한줄 소개를 자유롭게 수정하세요 -->
> 한줄 소개: 여기에 원하는 소개 문장을 입력하세요.

[![Profile README](https://img.shields.io/badge/Profile-@tlrma-181717?style=for-the-badge&logo=github)](https://github.com/tlrma)
[![Email](https://img.shields.io/badge/Email-your_email_here-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:your_email_here)
[![Status](https://img.shields.io/badge/Focus-Embedded%20%26%20AI-0A66C2?style=for-the-badge)](#)

</div>

---

## 🙋 Introduction

임베디드 시스템과 AI를 결합한 문제 해결에 관심이 있습니다.  
센서 기반 제어, computer vision, ROS, 웹 서비스 개발 경험을 바탕으로 실제 환경에서 동작하는 시스템을 구현해 왔습니다.

---

## 🧰 Tech Stack

<div align="center">

[![My Skills](https://skillicons.dev/icons?i=c,cpp,python,linux,flask,sqlite)](https://skillicons.dev)

<br>
<br>

![ROS](https://img.shields.io/badge/ROS-22314E?style=for-the-badge&logo=ros&logoColor=white)

</div>

---

## 🚀 Projects

### 🛴 ATmega128을 사용한 안전한 전동 킥보드 시스템

**문제 정의**  
최소한의 안전 수칙을 지키지 않아 더 큰 사고로 이어지는 상황을 줄이기 위해, 안전 조건을 만족해야만 작동하는 킥보드 시스템을 구현했습니다.

**핵심 기능**
- 헬멧 착용 여부 확인
- 음주 수치 측정
- 양손 핸들링 확인
- 운행 시간 및 요금 계산
- 자동 조명 제어
- 헬멧부 ↔ 킥보드부 간 UART 통신

**시스템 구성**
- **헬멧부**
  - 스위치 센서를 이용한 헬멧 착용 여부 확인
  - MQ3 센서를 이용한 음주 수치 측정
  - 측정 데이터를 킥보드부로 전송
- **킥보드부**
  - 손잡이 양쪽 터치 센서를 이용한 양손 핸들링 확인
  - 운행 시간, 요금, 조명 제어
  - 주행 중에도 안전 조건을 지속적으로 검사
  - 조건 위반 시 운행 종료 후 요금 정산

**사용 기술**  
![ATmega128](https://img.shields.io/badge/ATmega128-5C3EE8?style=flat-square)
![MQ3](https://img.shields.io/badge/MQ3%20Alcohol%20Sensor-0A66C2?style=flat-square)
![Switch](https://img.shields.io/badge/Switch%20Sensor-2EA44F?style=flat-square)
![Touch](https://img.shields.io/badge/Touch%20Sensor-8250DF?style=flat-square)
![UART](https://img.shields.io/badge/UART%20Communication-6F42C1?style=flat-square)

**기여도**
- 헬멧 착용 여부 확인: 10/10
- 음주 수치 측정: 10/10
- 양손 핸들링 확인: 5/10
- UART 통신: 10/10

**문제 해결**
1. 머리카락 때문에 터치 센서가 정확히 동작하지 않는 문제가 있었습니다.  
   → 헬멧은 머리에 밀착 착용하는 것이 올바르다는 점을 반영해 스위치 센서로 지속 확인하도록 변경했습니다.
2. 헬멧부와 킥보드부 간 데이터 전송 시 여러 값을 개별 전송하면 지연이 발생했습니다.  
   → 알코올 수치와 헬멧 착용 여부 데이터를 하나로 통합하고 타이머 기반으로 전송해 지연을 줄였습니다.

---

### 🚁 타겟 드론 Following 드론 시스템

**문제 정의**  
비행 중인 타겟 드론을 안정적으로 인식하고 자동으로 추적하는 시스템을 구현했습니다.

**핵심 기능**
- 드론 데이터셋 기반 타겟 드론 감지 모델 학습
- 전면 카메라 영상에서 타겟 드론 탐지
- bounding box 크기와 좌표를 기반으로 위치 조정
- ROS 토픽 발행을 통한 제어 명령 전달

**사용 기술**  
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![ROS](https://img.shields.io/badge/ROS-22314E?style=flat-square&logo=ros&logoColor=white)
![Detection](https://img.shields.io/badge/Object%20Detection-DB4437?style=flat-square)
![Jetson](https://img.shields.io/badge/Jetson%20Nano-76B900?style=flat-square&logo=nvidia&logoColor=white)

**기여도**
- 모델 학습: 8/10
- 위치 제어 알고리즘: 8/10
- 파이프라인 구성: 10/10
- 최적화: 10/10

**문제 해결**
1. Jetson Nano에서 이미지 분석부터 위치 조절까지의 처리 속도가 느려 버퍼링과 인식률 저하가 발생했습니다.  
   → 모든 센서 스트리밍 구조를 점검하고 카메라 프레임 수를 조정해 최적화했습니다.
2. 드론의 불안정한 비행으로 통신까지 불안정해지는 문제가 있었습니다.  
   → 하드웨어를 물리적으로 더 단단하게 결합해 안정성을 높였습니다.
3. 제어 방식에 대해 속도 제어와 위치 제어 사이에서 팀 내 의견 차이가 있었습니다.  
   → 두 방식을 모두 실험하고 실제 안정성을 비교한 뒤 속도 제어 방식을 채택했습니다.

---

### 🎵 Facial Emotion Detect 노래 추천 웹사이트

**문제 정의**  
사용자의 표정에서 감정을 예측하고, 사용자 이력까지 반영해 감정 기반 음악을 추천하는 웹사이트를 구현했습니다.

**핵심 기능**
- ResNet18 기반 얼굴 표정 인식 및 감정 예측
- K-NN 기반 사용자 식별
- Spotify API 기반 음악 추천 및 재생
- Flask 기반 웹페이지 구현
- SQLite3 기반 이용 기록 저장

**사용 기술**  
![ResNet18](https://img.shields.io/badge/ResNet18-1F6FEB?style=flat-square)
![KNN](https://img.shields.io/badge/K--NN-8250DF?style=flat-square)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![SQLite3](https://img.shields.io/badge/SQLite3-003B57?style=flat-square&logo=sqlite&logoColor=white)
![Spotify](https://img.shields.io/badge/Spotify%20API-1DB954?style=flat-square&logo=spotify&logoColor=white)

**기여도**
- 감정 예측 모델 학습: 10/10
- 사용자 인식 모델 및 데이터베이스 구축: 10/10
- 웹페이지 구현: 5/10

**문제 해결**
1. 초기 표정 인식 모델의 정확도가 낮았습니다.  
   → 기존 데이터셋이 서양인 및 흑백 위주라는 점을 분석했습니다.  
   → 동양인 비중이 높은 데이터셋을 추가하고, angry / neutral 클래스 수 불균형을 확인했습니다.  
   → 가중치 조정과 data augmentation(cut-out, crop, noise 등)을 적용해 모든 클래스에서 85% 이상의 정확도를 달성했습니다.
2. 사용자 식별에 ResNet 계열 모델을 사용하면 재학습 시간이 길고 데이터도 충분하지 않았습니다.  
   → K-NN을 활용해 빠르게 사용자 데이터를 구축하는 방식으로 전환했습니다.

---

## 🏃 Activities

<table>
<tr>
<td width="33%" valign="top">

### 🌱 NCOSS 서포터즈
**기간**  
2024.03 ~ 2024.08

**키워드**  
오픈소스, 콘텐츠 제작, 기술 홍보

</td>
<td width="33%" valign="top">

### 🤝 한국장학재단 대학생 재능봉사 캠프
**기간**  
2024.02.12 ~ 2024.02.15

**키워드**  
교육 봉사, 팀 활동, 나눔

</td>
<td width="33%" valign="top">

### 💻 소모임 C언어 세미나
**기간**  
2021.09 ~ 2023.12

**키워드**  
기초 프로그래밍, 발표, 스터디 운영

</td>
</tr>
</table>

---

## 📌 Repository Guide

- `tlrma` 저장소: GitHub 프로필 메인 소개용 README
- `my-portfolio` 저장소: 프로젝트와 활동을 자세히 정리한 포트폴리오 README

---

## 📬 Contact

- Email: `your_email_here`
- GitHub: `https://github.com/tlrma`

<!-- 필요하면 아래 항목을 추가하세요 -->
<!-- Blog: -->
<!-- Notion: -->
