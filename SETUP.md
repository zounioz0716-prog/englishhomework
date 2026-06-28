# 김규리쌤 공부방 — 설치 안내

이상한영어 숙제방과 동일한 프로그램을 김규리선생님 계정으로 새로 연결하는 가이드입니다.
모든 계정은 **김규리선생님 구글 이메일**로 가입하세요.

## 준비된 파일 (이 폴더)
- `study.html` — 메인 프로그램 (아래 3곳 자리표시자만 채우면 됨)
- `api/tutor.js` — AI 튜터 중계(Vercel용, 수정 불필요)
- `study-og.png` — 카톡 공유 썸네일
- `favicon*` , `apple-touch-icon.png` — 아이콘

## study.html에서 채워야 할 자리표시자 3곳
1. `const FIREBASE_CONFIG = { ... }` — Firebase 웹앱 설정 (2단계에서)
2. `const AI_ENDPOINT = ""` — Vercel 주소 `https://...vercel.app/api/tutor` (3단계에서)
3. `const KAKAO_CHANNEL = "...";` — 김규리쌤 카카오 채널 주소
4. (선택) `og:image` / `twitter:image` 의 `https://CHANGE-ME-DOMAIN/study-og.png` → 실제 사이트 주소로

---

## 1단계: GitHub (사이트 호스팅)
1. github.com 가입(김규리 구글 이메일) → 새 저장소 `gyuri-study` (Public)
2. 이 폴더의 파일 전부 업로드 (Add file → Upload files)
3. Settings → Pages → Branch: main → 저장 → 사이트 주소 확인 (`https://<id>.github.io/gyuri-study/`)

## 2단계: Firebase (진행 동기화 + 선생님 대시보드)
1. console.firebase.google.com → 프로젝트 만들기 (예: gyuri-study)
2. Firestore Database → 만들기 → 위치 asia-northeast3(서울) → 테스트 모드
3. Authentication → 시작하기 → 익명 사용 설정
4. ⚙️ 프로젝트 설정 → 웹앱(</>) 추가 → 나온 `firebaseConfig` 를 study.html에 붙여넣기
5. Authentication → 설정 → 승인된 도메인에 GitHub Pages 주소(또는 커스텀 도메인) 추가
6. (운영 후) Firestore 규칙을 인증필수로 교체

## 3단계: Vercel (AI 회화 튜터)
1. vercel.com 가입(GitHub로) → Add New Project → `gyuri-study` Import
2. Environment Variables: `ANTHROPIC_API_KEY` = 김규리쌤 클로드 키
3. Deploy → 주소(`https://...vercel.app`) → `/api/tutor` 를 study.html AI_ENDPOINT에 입력

## 4단계: 카카오 채널
김규리쌤 카카오 채널 주소(`http://pf.kakao.com/_xxxx`)를 KAKAO_CHANNEL에 입력

## 5단계: 마무리
- study.html 다시 업로드(자리표시자 다 채운 버전)
- 학생 등록 → 링크 전송 → 끝!
