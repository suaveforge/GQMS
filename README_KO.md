# G-QMS 정적 제안 데모

넥스콘테크놀러지 G-QMS 1차 사업 제안용 정적 웹 데모입니다.

## 특징
- 별도 빌드 없이 `index.html`만으로 실행
- 한국어 / English / Tiếng Việt 전환
- 반응형 PC·태블릿·모바일 UI
- 통합 대시보드, 공정 현황, 품질 분석, 현장 입력, 수집 관리, 보고서, 기준 정보
- 외부 CDN·유료 라이브러리 없음
- PWA 캐시 적용

## 로컬 실행
정적 파일은 `file://`로 열기보다 로컬 서버 사용을 권장합니다.

### Python
```bash
python -m http.server 8080
```
브라우저에서 `http://localhost:8080`

### Node
```bash
npx serve .
```

## GitHub Pages 배포
1. 새 GitHub 저장소 생성
2. 본 폴더의 파일 전체를 저장소 루트에 업로드
3. 기본 브랜치를 `main`으로 사용
4. GitHub 저장소 `Settings → Pages → Source`에서 `GitHub Actions` 선택
5. `main` 푸시 후 Actions 완료 대기

`.github/workflows/pages.yml`이 자동 배포합니다.

## 서브도메인 연결
예: `qms.example.com`

1. 저장소 `Settings → Pages → Custom domain`에 서브도메인 입력
2. DNS 관리 화면에서 CNAME 추가
   - Name: `qms`
   - Target: `<GitHub사용자명>.github.io`
3. DNS 적용 후 `Enforce HTTPS` 활성화

`CNAME.example` 파일을 참고하여 실제 도메인으로 이름을 `CNAME`으로 변경할 수 있습니다.

## 현재 범위
정적 제안용 UI이며 MES·설비·DB 실제 연동은 포함하지 않습니다. 실제 구축 시 API와 데이터 수집 어댑터를 연결하도록 화면 구조를 분리했습니다.


## v2 상호작용
- 통합/천안/베트남 전환 시 KPI, 그래프, 라인, 공정, 수집 데이터가 실제 변경됩니다.
- 공정 필터와 검색, 분석 조건, 새로고침이 동작합니다.
- 사진은 브라우저에서 압축 후 IndexedDB에 저장하고, 쿠키에는 사진 ID와 메타데이터를 저장합니다.
- 보고서 다운로드는 실제 CSV 파일을 생성합니다.
- 수집 상세, 알림, 기준정보 탭/추가 기능이 동작합니다.


## V3 산업용 대형 UI 기준
- 기본 본문 16px
- 표와 필터 14~15px
- 페이지 제목 28px
- 입력창·일반 버튼 48~50px
- 현장 판정 버튼 96px
- 10인치 태블릿 중심 반응형
- 모바일 공정·수집 표는 가로 스크롤 대신 카드형 전환


## V4 변경
- 이전보다 확실히 큰 18px 기본 본문
- 페이지 제목 34px
- 필터·입력창·버튼 56px
- 공정 목록 표 16px / 행 높이 70px
- 현장 PASS/FAIL 버튼 112px
- 기존 서비스워커 캐시 자동 해제
- CSS/JS 버전 쿼리로 브라우저 강제 갱신
