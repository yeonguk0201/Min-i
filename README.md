# 📸 Memory Album (추억앨범)

> 가족, 친구들과 함께 만드는 AI 기반 추억 공유 플랫폼

## 📋 프로젝트 개요

Memory Album은 그룹 단위로 사진을 공유하고, AI가 생성한 질문에 답변하며 추억을 기록하는 웹 애플리케이션입니다. 음성 인식과 AI 스토리 생성 기능을 통해 더욱 풍부한 추억 기록을 제공합니다.

## ✨ 주요 기능

### 1. 사용자 인증 및 관리

- **회원가입/로그인**: 이메일 기반 회원가입 및 로그인
- **프로필 관리**: 프로필 이미지 업로드 및 정보 수정
- **비밀번호 변경**: 계정 보안 관리
- **자동 로그인**: 쿠키 기반 세션 관리

### 2. 그룹 관리

- **그룹 생성**: 그룹명, 설명, 이미지 설정
- **그룹 참가**: 초대 코드를 통한 그룹 참가
- **멤버 관리**: 그룹 멤버 조회, 초대, 추방 기능
- **그룹 전환**: 여러 그룹 간 전환 가능
- **그룹 정보 수정**: 그룹명, 설명, 이미지 수정

### 3. 앨범 관리

- **앨범 생성**: 테마 선택 및 앨범 정보 설정
- **앨범 목록**: 그리드 레이아웃으로 앨범 조회
- **앨범별 사진 관리**: 앨범별로 사진 분류 및 관리
- **앨범 썸네일**: 최근 업로드된 사진으로 앨범 썸네일 자동 생성

### 4. 미디어 업로드 및 관리

- **사진 업로드**: 다중 이미지 업로드 지원
- **사진 상세 보기**:
  - Embla Carousel을 활용한 슬라이더 뷰
  - 작성자, 업로드 날짜 정보 표시
  - 좋아요 기능
  - 사진 다운로드
- **스토리 보기**: 각 사진에 대한 AI 생성 스토리 확인
- **좋아요 기능**: 사진에 좋아요 표시 및 좋아요 목록 조회

### 5. 질문 및 답변 시스템

- **질문 생성**:
  - 사진과 함께 질문 업로드
  - 앨범 소유자(OWNER)가 질문 생성
- **답변 작성**:
  - 텍스트 입력
  - 음성 녹음 및 자동 텍스트 변환 (STT)
  - 실시간 음성 재생
- **답변 목록**:
  - 무한 스크롤 구현
  - 검색 기능 (작성자명, 질문 내용)
- **AI 스토리 생성**: 답변 기반 자동 스토리 생성

### 6. 홈 대시보드

- **최근 콘텐츠**: 최근 업로드된 사진 5개 캐러셀
- **앨범 미리보기**: 앨범 목록 및 최근 사진 조회
- **빠른 액세스**: 질문 만들기, 초대하기, 참가하기 버튼

### 7. 기타 기능

- **검색 기능**: 질문 및 답변 검색 (디바운싱 적용)
- **반응형 디자인**: 모바일 및 데스크톱 최적화
- **무한 스크롤**: React Intersection Observer 활용
- **상태 관리**: Zustand를 활용한 전역 상태 관리
- **데이터 페칭**: React Query를 활용한 서버 상태 관리

## 🛠 기술 스택

### Frontend

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **UI Components**:
  - Radix UI
  - shadcn/ui
  - Custom Components
- **State Management**:
  - Zustand (전역 상태)
  - React Query (서버 상태)
- **Form Management**: React Hook Form + Zod
- **Carousel**: Embla Carousel
- **Icons**:
  - Lucide React
  - React Icons
  - Hugeicons React

### 주요 라이브러리

- `@tanstack/react-query`: 서버 상태 관리 및 캐싱
- `zustand`: 클라이언트 상태 관리
- `react-hook-form`: 폼 관리
- `zod`: 스키마 검증
- `embla-carousel-react`: 이미지 캐러셀
- `react-responsive-masonry`: 반응형 그리드 레이아웃
- `axios`: HTTP 클라이언트
- `js-cookie`: 쿠키 관리
- `dayjs`: 날짜 처리

## 📁 프로젝트 구조

```
src/
├── app/                    # Next.js App Router 페이지
│   ├── groups/            # 그룹 관련 페이지
│   │   ├── [id]/          # 동적 그룹 라우트
│   │   │   ├── albums/    # 앨범 관리
│   │   │   ├── dashboard/ # 그룹 대시보드
│   │   │   ├── members/   # 멤버 관리
│   │   │   └── questions/ # 질문 목록
│   │   ├── create/        # 그룹 생성
│   │   └── join/          # 그룹 참가
│   ├── home/              # 홈 대시보드
│   ├── likes/             # 좋아요 목록
│   ├── profile/           # 프로필 관리
│   ├── login/             # 로그인
│   └── signup/            # 회원가입
├── components/            # 재사용 가능한 컴포넌트
│   ├── albums/           # 앨범 관련 컴포넌트
│   ├── common/            # 공통 컴포넌트
│   ├── embla/             # 캐러셀 컴포넌트
│   ├── messages/          # 메시지/답변 컴포넌트
│   ├── photoDetail/       # 사진 상세 컴포넌트
│   └── ui/                # UI 기본 컴포넌트
├── features/              # 기능별 API 모듈
│   ├── album/             # 앨범 API
│   ├── auth/              # 인증 API
│   ├── group/             # 그룹 API
│   ├── media/             # 미디어 API
│   └── member/            # 멤버 API
├── lib/                   # 유틸리티 함수
│   ├── albums/            # 앨범 관련 유틸
│   ├── image/             # 이미지 처리
│   └── search/             # 검색 관련
├── services/              # 서비스 레이어
│   ├── auth.ts            # 인증 서비스
│   └── groupJoin.ts       # 그룹 참가 서비스
├── store/                 # Zustand 스토어
│   ├── useAlbumStore.ts   # 앨범 상태
│   ├── useGroupStore.ts   # 그룹 상태
│   ├── useMessageStore.ts # 메시지 상태
│   ├── useUserInfo.ts     # 사용자 정보
│   └── useViewStore.ts    # 뷰 상태
└── model/                 # 타입 정의
    └── user.ts            # 사용자 모델
```

## 🎯 핵심 기능 상세

### 1. 음성 인식 기능

- **MediaRecorder API**를 활용한 실시간 음성 녹음
- WebM 형식으로 녹음 후 서버로 전송
- **Speech-to-Text API**를 통한 자동 텍스트 변환
- 녹음 재생 및 삭제 기능

### 2. AI 스토리 생성

- 사용자의 답변을 기반으로 AI가 자동으로 스토리 생성
- 생성된 스토리는 사진과 함께 저장되어 추억으로 기록

### 3. 역할 기반 접근 제어

- **OWNER**: 그룹 소유자, 질문 생성 및 앨범 관리 권한
- **MEMBER**: 그룹 멤버, 질문에 답변하는 권한

### 4. 실시간 UI 업데이트

- React Query의 `invalidateQueries`를 활용한 자동 데이터 갱신
- Optimistic Updates로 사용자 경험 향상

## 🚀 시작하기

### 필수 요구사항

- Node.js 18 이상
- npm 또는 yarn

### 설치 및 실행

```bash
# 의존성 설치
npm install

# 개발 서버 실행
npm run dev

# 프로덕션 빌드
npm run build

# 프로덕션 서버 실행
npm start
```

### 환경 변수 설정

`.env.local` 파일을 생성하고 다음 변수들을 설정하세요:

```env
# 백엔드 API URL
NEXT_PUBLIC_API_URL=your_backend_url

# 개발 환경 설정
NEXT_PUBLIC_USE_MOCK_DATA=false
NEXT_PUBLIC_SKIP_AUTH=false
```

## 📱 주요 화면

### 홈 화면

- 그룹 정보 및 최근 콘텐츠 표시
- 빠른 액세스 버튼 (질문 만들기, 초대하기 등)

### 앨범 목록

- 그리드 레이아웃으로 앨범 표시
- 각 앨범의 최근 사진 썸네일

### 사진 상세

- 캐러셀을 통한 사진 탐색
- 좋아요, 다운로드, 스토리 보기 기능

### 질문/답변

- 질문 목록 및 검색
- 텍스트/음성 답변 작성
- AI 스토리 생성

## 📸 예시화면

1. **홈 대시보드** (`/home`)

   - 그룹 정보 헤더
   - 최근 콘텐츠 캐러셀
   - 액션 버튼들 (질문 만들기, 초대하기 등)
   - 
<img width="194" height="423" alt="Image" src="https://github.com/user-attachments/assets/bfa7b97a-b454-4d0b-b584-d66411d4a982" />

2. **앨범 목록** (`/groups/[id]/albums`)

   - 그리드 레이아웃의 앨범 카드들
   - 각 앨범의 썸네일 이미지들
   - 
<img width="194" height="423" alt="Image" src="https://github.com/user-attachments/assets/7a7d7aa6-fb9d-4430-8335-148a3fa5eb77" />
<img width="195" height="425" alt="Image" src="https://github.com/user-attachments/assets/ffaeffbe-2449-40e4-bbe0-ccb810fca21e" />

3. **사진 상세 (캐러셀)** (`/groups/[id]/albums/[albumId]/photo/[photoId]`)

   - Embla Carousel을 활용한 스와이프 가능한 사진 뷰
   - 좋아요 버튼, 작성자 정보, 스토리 보기 기능

<img width="193" height="424" alt="Image" src="https://github.com/user-attachments/assets/5f17d59c-4f3a-4a8e-87d8-6fab4239f0e5" />
<img width="194" height="423" alt="Image" src="https://github.com/user-attachments/assets/19b21dcb-3b1b-4d11-beb4-20dd98e6649d" />

4. **프로필 및 그룹 관리** (`/profile`)
   - 사용자 정보
   - 참여 중인 그룹 목록
   - 그룹 전환 기능
     
<img width="194" height="423" alt="Image" src="https://github.com/user-attachments/assets/fb899b66-9ef4-4247-97ec-9b3e193bb88b" />

## 🔒 보안 기능

- JWT 토큰 기반 인증
- 쿠키를 통한 세션 관리
- 미들웨어를 통한 라우트 보호
- CORS 설정

## 🎨 UI/UX 특징

- **반응형 디자인**: 모바일 우선 설계
- **직관적인 네비게이션**: GNB/FNB를 통한 쉬운 이동
- **부드러운 애니메이션**: Tailwind CSS transitions
- **접근성**: Radix UI 기반 접근 가능한 컴포넌트

## 📝 개발 노트

### 상태 관리 전략

- **Zustand**: 클라이언트 상태 (사용자 정보, 그룹 정보, 앨범 정보)
- **React Query**: 서버 상태 (API 데이터, 캐싱, 동기화)

### 성능 최적화

- 이미지 최적화 (Next.js Image 컴포넌트)
- 코드 스플리팅 (Next.js App Router)
- 무한 스크롤을 통한 점진적 로딩
- React Query 캐싱

### 코드 품질

- TypeScript를 통한 타입 안정성
- ESLint + Prettier를 통한 코드 포맷팅
- 컴포넌트 기반 아키텍처

## 🚧 기술적 도전과제 및 해결 방법

프로젝트 개발 중 마주한 주요 기술적 도전과제들과 해결 과정을 정리했습니다.

### 1. 배포 시 빌드 오류 및 환경 변수 문제

**문제점:**

- 프로덕션 빌드 시 환경 변수가 제대로 로드되지 않음
- 빌드 타임과 런타임 환경 변수 처리 차이
- Next.js의 서버/클라이언트 컴포넌트에서 환경 변수 접근 방식 차이

**해결 방법:**

- `NEXT_PUBLIC_` 접두사를 사용하여 클라이언트에서 접근 가능한 환경 변수 명시
- `.env.local`, `.env.production` 파일을 분리하여 환경별 설정 관리
- Vercel 등의 배포 플랫폼에서 환경 변수를 직접 설정
- 빌드 전 환경 변수 검증 스크립트 추가

```typescript
// 환경 변수 타입 안정성을 위한 설정
const isDevelopment = process.env.NODE_ENV === 'development';
const useMockData =
  process.env.NEXT_PUBLIC_USE_MOCK_DATA === 'true' || isDevelopment;
```

### 2. 사진 슬라이더 스와이프 시 URL 자동 갱신

**문제점:**

- Embla Carousel로 사진을 스와이프할 때 URL이 변경되지 않아 브라우저 뒤로가기/앞으로가기 시 문제 발생
- 공유 링크를 클릭했을 때 해당 사진으로 바로 이동하지 못함
- URL과 현재 보이는 사진이 동기화되지 않음

**해결 방법:**

- `window.history.replaceState`를 활용하여 URL을 업데이트하되 페이지 리로드 없이 처리
- Embla Carousel의 `select` 이벤트를 감지하여 현재 인덱스에 맞는 URL로 자동 갱신
- 초기 로드 시 URL의 `photoId`를 파싱하여 해당 인덱스로 캐러셀 이동

```typescript
// PhotoDetail.tsx
const updateURL = useCallback(
  (index: number) => {
    if (!images[index]) return;
    const newPhotoId = images[index].id.toString();
    const newPath = `/groups/${groupId}/albums/${albumId}/photo/${newPhotoId}`;
    window.history.replaceState(null, '', newPath);
  },
  [albumId, groupId, images],
);

useEffect(() => {
  if (!emblaApi) return;

  const handleSelect = () => {
    const selectedIndex = emblaApi.selectedScrollSnap();
    updateURL(selectedIndex);
  };

  emblaApi.on('select', handleSelect);

  return () => {
    emblaApi.off('select', handleSelect);
  };
}, [emblaApi, updateURL]);
```

**결과:**

- 스와이프할 때마다 URL이 자동으로 업데이트되어 브라우저 히스토리 관리가 정상 작동
- 특정 사진 링크를 공유하면 해당 사진으로 바로 이동 가능
- 브라우저 뒤로가기/앞으로가기 버튼으로 사진 간 이동 가능

### 3. 그룹별 UI 상태 분리 및 데이터 섞임 방지

**문제점:**

- 사용자가 여러 그룹에 속해 있을 때 그룹을 전환하면 이전 그룹의 데이터가 남아있음
- React Query 캐시가 그룹별로 분리되지 않아 잘못된 데이터가 표시됨
- Zustand 스토어의 상태가 그룹 전환 시 초기화되지 않음

**해결 방법:**

- **그룹 ID를 React Query 키에 포함**: 모든 쿼리 키에 `groupId`를 포함하여 그룹별로 캐시 분리
- **그룹 전환 시 명시적 캐시 무효화**: `queryClient.invalidateQueries()`로 이전 그룹 데이터 제거
- **Zustand 스토어 초기화**: 그룹 전환 시 관련 스토어 상태 초기화
- **현재 그룹 ID 관리**: `useUserStore`의 `currentGroupId`를 중앙에서 관리하여 일관성 유지

```typescript
// 그룹별 쿼리 키 구조
const queryKey = ['groups', groupId, 'albums', albumId, 'media'];

// 그룹 전환 시
const handleSetCurrentGroup = () => {
  if (window.confirm('현재 그룹으로 설정하시겠습니까?')) {
    // 1. 이전 그룹의 캐시 무효화
    queryClient.invalidateQueries({
      queryKey: ['groups', previousGroupId],
    });

    // 2. 현재 그룹 ID 업데이트
    setCurrentGroupId(Number(groupId));

    // 3. 관련 스토어 초기화
    clearGroup();
    refreshAlbums();

    router.push('/home');
  }
};

// useEffect로 그룹 ID 변경 감지
useEffect(() => {
  if (groupId) {
    // 그룹별 데이터 페칭
    fetchGroupData();
    fetchAlbums();
  }
}, [groupId]);
```

**결과:**

- 그룹 전환 시 이전 그룹의 데이터가 완전히 제거되고 새 그룹 데이터만 표시
- React Query 캐시가 그룹별로 독립적으로 관리되어 데이터 혼선 방지
- 사용자가 어떤 그룹에 있든 항상 올바른 데이터만 보게 됨

### 4. 추가 개선 사항

- **무한 스크롤 최적화**: React Intersection Observer를 활용하여 성능 최적화
- **이미지 로딩 최적화**: Next.js Image 컴포넌트와 lazy loading 적용
- **에러 핸들링**: 각 API 호출에 대한 에러 바운더리 및 폴백 UI 구현

## 🤝 기여하기

이 프로젝트는 팀 프로젝트로 개발되었습니다. 기여 방법:

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 라이선스

이 프로젝트는 팀 프로젝트입니다.

## 👥 팀원

- Frontend Developer  김영욱 이윤경
- Backend Developer   김동현 우연정

---

**Made with ❤️ by Memory Album Team**
