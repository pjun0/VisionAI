# 얼굴 인식 프로젝트
1. 프로젝트 주제 및 목적
   - 한국인 데이터셋 얼굴 인식
   
3. 프로젝트 진행
   - 시각인공지능 전공 팀프로젝트(3인)
   - 2022.11 ~ 2022.12

4. 프로젝트 설명

   ![image](https://github.com/user-attachments/assets/a334b1f6-4fa2-45f5-af36-fbc7789cc581)

   Ai hub의 한국인 얼굴 데이터셋을 사용해 이미지 내 고유코드를 기준으로 인물 라벨링을 하여 총 133명, 2413개의 얼굴 이미지 데이터셋을 만들었다. 이후 이미지의 노이즈를 줄이는 Face alignment 과정에서 Dlib, YoloDetector, MTCNN을 사용해보았을때 시간측면에서는 Dlib과 YoloDetector가 유리했으나 정확도 측면에서 MTCNN이 우수해 MTCNN을 사용했다. 추가적으로 외국인 얼굴 데이터에도 적용해보기 위해 LFW Dataset(Labeled Faces in the Wild Dataset)을 사용했다. 또 학습데이터가 부족한 점을 고려하여 데이터 Input 형식(A, P, N)의 조합 방식을 늘려 Input data의 수를 늘렸다.

   분류에 앞서 Encoder는 데이터가 적은 것을 고려하여 ImageNet데이터로 사전학습된 Xception모델에 레이어를 추가해서 사용했다. 학습모델은 Siamese Network 구조로 Triplet loss를 손실함수를 사용했다. Triplet loss는 기준이 되는 이미지인 A, 긍정이미지인 P, 부정이미지인 N이 있을 때, A와 P의 거리가 항상 A와 N의 거리보다 작거나 같게 만드는 것을 목표로 한다.
   ${\textsf{\color{magenta}(A와 P가 거리가 멀고 A와 N이 거리가 가까울수록 모델의 분류 성능은 더 좋아지는데 학습 데이터가 적다는 이유로 데이터 조합 방식을 무작}}$ ${\textsf{\color{magenta}정 늘리지 않았더라면 성능이 더 좋지 않았을까 하는 아쉬움이 있다.)}}$

   인물 예측에는 KNN, SVM, RandomForest 모델을 사용했다. 예측 성능이 가장 좋은 RandomForest모델을 최종 예측 모델로 사용하였고 한국인 얼굴 정면, 좌측, 우측 사진 각각 25개 중 18개, 17개, 14개를 인식하였다. 정면 사진은 72%의 정확도를 보여준 반면 측면은 68%, 56%의 정확도를 보였는데 이는 측면사진에 절반 정도 배경이 차지하고 있어 얼굴의 특징점을 잡아내는 데 어려움이 있었던 것으로 예상된다.
   
 
5. 프로젝트 역할
    - 한국인 얼굴 데이터셋, LFW Dataset 라벨링 및 데이터셋 생성
    - Face alignment과정 Dlib, MTCNN, Yoloface 비교실험
    - triplet loss의 다양한 Anchor, Positive, Negative 쌍 구성
    - Encoder, Siamese network, Triplet Loss 구현

8. 프로젝트 결과
   
    - https://drive.google.com/file/d/113NOlGnUgH1SpVyF-6goxK2NIG1nrwWq/view?usp=drive_link
    
   
