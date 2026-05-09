# Claude Code로 데이터 분석 자동화하기 (B2G)

> **사업명**: 2026 중소기업 인재키움프리미엄 훈련
> **회차**: 4회 (3h × 4) · 비대면 실시간 (Zoom) · 인프런 운영
> **대상**: SQL/Python으로 데이터 분석하는 중소기업 실무자 (Claude Code는 처음)
> **메인 데이터**: 서울 미세먼지 (열린데이터광장 OA-2218) + 결합 (따릉이·지하철·날씨·언급량·쇼핑 적재본)

수강생용 공개 자료 모음. 매 회차 종료 후 본인 fork의 `day{n}/` 폴더에 산출물(CLAUDE.md, outputs, notes.md 등)을 push해서 미션 제출.

---

## 폴더 구조

```
b2g-claude-code-2026/
├── README.md                       # 본 문서 (폴더 구조 + 다운로드 안내)
├── data/                           # 강의에서 쓰는 모든 원본 데이터
│   ├── seoul_air_quality/          # 메인 — 미세먼지 (OA-2218)
│   │   ├── seoul_air_quality_2024.csv
│   │   └── seoul_air_quality_2025.csv
│   ├── seoul_districts/            # folium 지도용 GeoJSON
│   │   └── seoul_districts.geojson
│   ├── seoul_bike/                 # 따릉이 일별 대여 건수
│   │   └── seoul_bike_daily_2024.csv
│   ├── seoul_subway/               # 지하철 일별 총 승하차
│   │   └── seoul_subway_daily_total_2024.csv
│   ├── weather/                    # 기상청 ASOS 서울 일자료 (Day 2 결합용)
│   │   └── README.md               # ※ 강사 사전 배포 예정
│   └── buzz/                       # 검색량/언급량 (네이버 데이터랩·구글 트렌드)
│       └── README.md               # ※ 강사 사전 배포 예정
├── prompts/                        # 회차별 시연·미션 프롬프트 원본
│   ├── day1_setup_and_first_analysis.md
│   └── day2_eda_and_join.md
├── ppt/                            # 회차별 슬라이드 (수강생 배포본)
│   ├── b2g_day1_setup.pptx
│   └── b2g_day2_eda.pptx
├── day1/                           # 1일차 산출물 템플릿
│   ├── CLAUDE.md                   # 프로젝트 컨텍스트 메모 (1일차 버전)
│   ├── outputs/                    # 차트 PNG 등
│   └── notes.md                    # "평소 같으면 얼마나 걸렸을까?" 한 줄 소감
└── day2/                           # 2일차 산출물 템플릿
    ├── CLAUDE.md                   # 1일차 그대로 복사 + 누적 규칙 반영
    ├── outputs/
    └── notes.md
```

> 3일차/4일차 폴더는 해당 회차 시작 직전 추가됩니다.

---

## 메인 데이터 — 서울 미세먼지

| 항목 | 내용 |
|---|---|
| 출처 | 서울 열린데이터광장 — 일별 평균 대기환경 정보 |
| 페이지 | https://data.seoul.go.kr/dataList/OA-2218/S/1/datasetView.do |
| 회원가입 | 불필요 (CSV 즉시 다운로드) |
| 시간 범위 | 2024-01-01 ~ 2025-12-31 (731일 × 25개 자치구) |
| 행 수 | **18,275행** (2024: 9,150 + 2025: 9,125) |
| 인코딩 | **CP949** (EUC-KR 호환) |
| 컬럼 9개 | 측정일시, 권역명, 측정소명, 이산화질소(ppm), 오존(ppm), 일산화탄소(ppm), 아황산가스(ppm), 미세먼지(㎍/㎥), 초미세먼지(㎍/㎥) |
| 컬럼명 통일 | 2024 "미세먼지/초미세먼지" → 2025 "미세먼지농도/초미세먼지농도" 와 일치하도록 분석 시 통일 |

CSV는 `data/seoul_air_quality/`에 강사 백업본이 있다. 강의 시간엔 위 페이지에서 직접 다운로드를 권장.

---

## 회차별 흐름

| 회차 | 주제 | 미션 |
|---|---|---|
| Day 1 (5/12) | 환경 세팅 + 데이터 가져오기 | 질문 3개 + 결과 캡처 + CLAUDE.md → `day1/` 푸시 |
| Day 2 (5/14) | EDA + 결합 데이터 | 질문 5개 (단독 3 + 결합 2) + Colab + CLAUDE.md 누적 → `day2/` 푸시 |
| Day 3 (5/19) | 대시보드 만들기 (HTML + Streamlit) | TBD |
| Day 4 (5/21) | Skills + 결합 분석 + 의사결정 리포트 | TBD |

---

## 사용 방법

1. 본인 GitHub로 이 레포를 **Fork** (또는 clone)
2. Claude Desktop 앱에서 자연어로 Claude Code 설치 요청 (Day 1 PPT 참조)
3. 본인 작업 폴더에서 `claude` 실행 → 데이터·CLAUDE.md를 작업 폴더에 배치
4. 각 회차 끝나면 본인 fork의 해당 `day{n}/` 폴더에 산출물 push
5. push한 PR 또는 본인 fork 링크를 강의 채널에 공유 → 미션 제출 완료

---

## 라이선스

- 코드·프롬프트·교안: MIT
- 미세먼지 CSV: 서울 열린데이터광장 공공데이터 (출처 표기 권장)
- 지하철·따릉이 CSV: 서울시 공공데이터 (출처 표기 권장)
