
# 🛠 스마트 커피 주문 시스템 – 키오스크 앱

> 직관적인 UI/UX와 빠른 주문 시스템으로 커피 주문을 더 편리하게!

---

## 🚀 프로젝트 개요

이 프로젝트는 **커피 주문 대기 시간을 줄이고**, **사용자 친화적인 경험을 제공**하기 위해 개발된 키오스크 앱입니다.  
또한, “뜨거운 아이스 아메리카노” 같은 **모순된 주문 표현을 방지**하고 **운영 효율성**을 높이는 것을 목표로 합니다.

---

## 🎯 주요 목표

- ⏱ **대기 시간 최소화**: 빠르고 직관적인 주문 프로세스 구현  
- 🖱 **UI/UX 최적화**: 사용자 중심의 인터페이스 설계  
- 💳 **결제 및 포인트 시스템**: 다양한 결제 방식과 포인트 적립 기능 제공

---

## 👨‍👩‍👧‍👦 팀 구성 및 역할

| 이름     | 역할   | 주요 업무 |
|----------|--------|-----------|
| **김서임** | 팀장   | UI/UX 설계, 음료 옵션 선택 화면 개발, PPT 제작 및 발표 |
| **박은호** | 팀원   | 메인 화면 및 장바구니 기능, 데이터 처리 로직 개발 |
| **강연주** | 팀원   | 주문 내역 확인, 결제 기능, 포인트 적립 시스템 구현 |
| **윤준영** | 팀원   | 음료 메뉴 레이아웃 구현, UX 개선 및 버그 수정 |

---

## 📅 개발 일정

| 기간       | 작업 내용 |
|------------|-----------|
| **1~2일차** | 시스템 설계 및 아키텍처 정의, Android 프로젝트 초기 설정 |
| **3~4일차** | 기본 화면 구성, 데이터 구조 설정, 사용자 입력 처리 |
| **5~7일차** | 주문 확인 화면, 결제 기능, 오류 처리 |
| **8~10일차**| 결제 UI 개선, 사용자 피드백 반영, 알림 시스템 구현 |
| **11~14일차**| 시스템 테스트, UI 마감, 최종 배포 준비, 발표 자료 제작 |

---

## 📱 맡은 역할

### ✅ 음료 옵션 선택화면 프론트엔드 구현

- **음료 메뉴 선택을 위한 사각형 버튼 UI**  
  XML에서 `LinearLayout`, `GridLayout`, `CardView` 등을 사용해 **정사각형 버튼 구조**를 설계하였습니다.
- 버튼은 **크기, 색상, 선택 여부에 따라 동적 스타일 변경**되며, 터치 시 효과가 적용됩니다.

### 🧩 UI 레이아웃 구조

### 🎨  메뉴 옵션 선택 화면
사용자가 커피를 주문할 때 온도, 사이즈, 시럽, 얼음 양 등을 직관적으로 선택할 수 있는 기능을 제공합니다.

✔ 커스텀 대화창을 통해 옵션을 선택할 수 있음

✔ 사용자 경험을 고려하여 직관적인 UI 구성

✔ 폰트 설정을 적용하여 일관된 디자인 유지


```xml
// 메뉴를 하나 골랐을 때 나타나는 옵션 선택창 생성
public void buttonAddItem(View v) { 
    // 커스텀 대화메뉴 생성 후 띄우기 
    Dialog optionDialog = new Dialog(MenuActivity.this); 
    optionDialog.setContentView(R.layout.activity_option); 
    optionDialog.show();
    resetSelections(); 

    // activity_option.xml 에 있는 UI 요소 아이디 가져오기
    selectMenuPrice = optionDialog.findViewById(R.id.selectMenuPrice);
    selectMenuName = optionDialog.findViewById(R.id.selectMenuName);
    btnComplete = optionDialog.findViewById(R.id.btn_complete);
    TextViewCoffeeInfo = optionDialog.findViewById(R.id.TextViewCoffeeInfo);

    // 폰트 설정
    Typeface customFont = Typeface.createFromAsset(getAssets(), "fonts/NanumBarunGothic-YetHangul.ttf");
    btnComplete.setTypeface(customFont);
    btnComplete.setEnabled(false);

    // 선택한 메뉴를 배열에 저장하고 화면에 보여줌
    buttonAddItem1 = findViewById(R.id.buttonAddItem1);
    buttonAddItem2 = findViewById(R.id.buttonAddItem2);
}

    <!-- 다른 메뉴들도 동일하게 반복 -->
```

- 🔥 HOT / ICE 선택 – 버튼 클릭으로 원하는 온도 설정
- 📏 사이즈 선택 – SMALL, MEDIUM, LARGE 옵션 제공
- 🍯 시럽 선택 – 바닐라, 헤이즐넛 등 추가 가능
- ❄️ 얼음 양 설정 – 기본값 또는 사용자 맞춤 설정

```
btnComplete.setOnClickListener(view2 -> {
    // 핫/아이스 선택 저장
    if (SelectedHot == 1) {
        menuOption1.add("HOT");
    } else if (SelectedHot == 2) {
        menuOption1.add("ICE");
    }

    // 사이즈 선택 저장
    if (SelectedSize == 1) {
        menuOption2.add("SMALL");
    } else if (SelectedSize == 2) {
        menuOption2.add("MEDIUM");
    } else if (SelectedSize == 3) {
        menuOption2.add("LARGE");
    }

    // 시럽 선택 저장
    if (SelectedTopping == 1) {
        menuOption3.add("바닐라 시럽");
    } else if (SelectedTopping == 2) {
        menuOption3.add("헤이즐넛 시럽");
    } else if (SelectedTopping == 3) {
        menuOption3.add("시럽 없음");
    }

    // 얼음 양 선택 저장
    if (SelectedIce == 1) {
        menuOption4.add("얼음양 없이");
    } else if (SelectedIce == 2) {
        menuOption4.add("얼음양 보통");
    } else if (SelectedIce == 3) {
        menuOption4.add("얼음양 많이");
    }

    // 최종 가격 업데이트
    menuPrice.set(menuPrice.size() - 1, menuPrice.get(menuPrice.size() - 1) + SelectedHotPrice + SelectedSizePrice + SelectedToppingPrice);

    // UI 업데이트
    adapter.notifyDataSetChanged();
    optionDialog.dismiss();
});

```

### ✅ 결제 및 포인트 시스템
- 선택 메뉴 확인 → 결제 → 포인트 적립까지 원스톱 프로세스

---

## 🛠 사용 기술

- Android Studio
- Java, XML
- RecyclerView, Fragment
- SQLite or Local Data Persistence
- 포인트 적립 및 결제 로직 구현

---

## 🎤 프로젝트 회고
이번 프로젝트를 통해 처음으로 안드로이드 스튜디오를 활용한 앱 개발에 도전했습니다. 실제 서비스에서 활용 가능한 키오스크 프로그램을 제작하면서, 사용자 관점에서 UI/UX를 설계하는 과정이 특히 흥미로웠습니다.
코드 작성 중 발생한 오류를 해결하고 디버깅을 반복하는 과정에서 많은 시행착오를 겪었지만, 최종적으로 완성된 코드가 정상적으로 작동했을 때의 성취감은 말로 표현할 수 없을 정도였습니다. 이 경험을 통해 안드로이드 개발의 기초를 탄탄히 다지는 계기가 되었고, 앞으로의 프로젝트에서도 이번 경험을 적극적으로 활용하고 싶습니다.


---

## 📎 참고 자료

- 📂 [프로젝트 발표 자료 다운로드](./키오스크_발표.pdf)
- 📑 [관련 레퍼런스 및 문서](https://help-center.payhere.in/feature/kiosk/customer)
