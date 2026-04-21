# 공통 UI 규칙 (미라이 프로젝트)

미라이 라이브챗 / 미라이챗 / 미라이스토어 등 여러 프로토타입 간 일관되게 적용할 UI 규칙.

---

## 헤더 콘텐츠명 (char-name) 반응형 말줄임

**규칙:**
- 모바일(< 431px): 12자 기준 말줄임 (`…`)
- 데스크탑(≥ 431px): 말줄임 해제, 전체 노출

**CSS:**
```css
.profile-pill .char-name{
  font-size:12px;
  color:var(--label-strong);
  letter-spacing:0.3px;
  max-width:156px;           /* ≈ 12자 @ 12px 폰트 */
  overflow:hidden;
  text-overflow:ellipsis;
  white-space:nowrap;
}

@media (min-width:431px){
  .profile-pill .char-name{
    max-width:none;
    overflow:visible;
    text-overflow:clip;
  }
}
```

**이유:** 콘텐츠명이 길어도 모바일 헤더가 깨지지 않고, 데스크탑은 공간 여유가 있어서 전체 보여줘도 괜찮음.

---

## 탑바 뒤로가기 아이콘

**규칙:**
- 배경 제거 (투명)
- SVG 체브론, stroke 2.5, 20x20
- 클릭 시 `scale(0.88)` 피드백

**HTML:**
```html
<button class="icon-btn" onclick="history.back()" aria-label="뒤로가기">
  <svg width="20" height="20" viewBox="0 0 24 24" fill="none"
       stroke="currentColor" stroke-width="2.5"
       stroke-linecap="round" stroke-linejoin="round">
    <path d="M15 18l-6-6 6-6"/>
  </svg>
</button>
```

**CSS:**
```css
.header .icon-btn{
  width:36px;height:36px;margin-left:-8px;
  background:transparent;padding:0;border:none;
  display:flex;align-items:center;justify-content:center;
  cursor:pointer;color:var(--label-normal);
  transition:all 0.2s;
}
.header .icon-btn:active{transform:scale(0.88)}
```

---

## 컬러 원칙

- **블루 베이스(slate) 금지**: `rgba(148,163,184,*)`, `rgba(186,196,210,*)` 같이 파란 기운 도는 중성색 사용 X
- 중성 그레이 필요 시: `rgba(190,190,190,*)`, `rgba(180,180,180,*)`, 혹은 미라이챗의 Cool-Neutral `rgba(174,176,182,*)` 등 사용
- 브랜드 색(민트, 골드)은 정상 사용

---

## 인디케이터 "진행 N/M"

**규칙:**
- "진행" 라벨: regular weight(400), 중성 그레이
- 숫자: bold(700), strong white
- 폰트 크기: 13px (라이브챗) / 12px (미라이챗) — 폰트 사이즈는 추후 통일 논의

**CSS 참고:**
```css
.dlg-progress-label{color:rgba(174,176,182,0.61);font-weight:400}
.dlg-progress-num{color:var(--label-strong);font-variant-numeric:tabular-nums;font-weight:700}
```

---

**Last Updated:** 2026-04-21
