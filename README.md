# Agent Studio · 윤승이네 가족

윤승이네 가족이 쓰는 AI 에이전트 지침 모음이에요.
랜딩페이지에서 엄마/아빠를 고르고 확인 번호를 누르면 에이전트 목록이 열려요.

| 에이전트 | 하는 일 | 지침 파일 |
|---|---|---|
| All time number one | 수업, 행정, 문서, 데이터 등 일반 업무 전부 | [agents/all-time-number-one.md](agents/all-time-number-one.md) |
| Skill Factory | Claude 스킬 제작, zip 파일 만들기 | [agents/skill-factory.md](agents/skill-factory.md) |
| webpage-agent | 업무용 웹페이지 제작 | [agents/webpage-agent.md](agents/webpage-agent.md) |

## 폴더 구조

```
agent-studio/
├─ index.html        ← 랜딩페이지 (잠금 화면 + 에이전트 목록)
├─ README.md         ← 지금 보고 있는 설명서
└─ agents/           ← 에이전트 지침 파일들
   ├─ all-time-number-one.md
   ├─ skill-factory.md
   └─ webpage-agent.md
```

## 처음 올리는 법 (GitHub 웹사이트에서, 코딩 없이)

1. github.com에 로그인 → 오른쪽 위 **+** → **New repository**
2. 이름에 `agent-studio` 입력 → **Create repository**
3. 만들어진 저장소 화면에서 **uploading an existing file** 클릭
4. 압축을 푼 `agent-studio` 폴더 **안의 내용물**(index.html, README.md, agents 폴더)을 끌어다 놓기
5. 아래 **Commit changes** 클릭 (커밋 = "여기까지 저장")
6. 저장소 위쪽 **Settings** → 왼쪽 **Pages**
7. Branch를 `main`, 폴더를 `/ (root)`로 고르고 **Save**
8. 1~2분 뒤 같은 화면 위쪽에 주소가 떠요: `https://내아이디.github.io/agent-studio/`

## 에이전트 추가하는 법

1. `agents` 폴더에 새 지침 파일(예: `new-agent.md`)을 올려요.
2. `index.html`을 열어 **연필 아이콘(Edit)** 클릭
3. `const AGENTS = [` 부분에 기존 덩어리 하나를 복사해 붙이고 `file`, `title`, `desc`, `tags`만 고쳐요.
4. **Commit changes** → 1~2분 뒤 페이지에 반영돼요.

## 확인 번호 바꾸는 법

페이지에는 번호 원문 대신 **해시**(번호를 알아볼 수 없게 바꾼 문자열)만 들어 있어요.

1. 아무 페이지에서 F12(개발자 도구) → **Console** 탭을 열어요.
2. 아래 줄을 붙여 넣고 `새번호` 자리에 네 자리 번호를 넣은 뒤 Enter:
   ```js
   crypto.subtle.digest("SHA-256", new TextEncoder().encode("agent-studio:새번호")).then(b=>console.log([...new Uint8Array(b)].map(x=>x.toString(16).padStart(2,"0")).join("")))
   ```
3. 나온 긴 문자열을 `index.html`의 `USERS` 안 `hash: "..."` 자리에 붙여 넣어요.

## 꼭 알아둘 점

- **이 잠금은 가벼운 문 역할만 해요.** GitHub Pages는 누구나 파일을 내려받을 수 있는 공개 사이트라서,
  주소를 아는 사람은 `agents/` 폴더의 파일을 직접 열 수 있어요. 네 자리 번호는 해시로 바꿔도 컴퓨터로 금방 맞힐 수 있어요.
- 그래서 **학생 개인정보, 비밀번호, API 키는 이 저장소에 절대 넣지 마세요.**
- **가족 안내 에이전트 지침은 올리지 마세요.** 그 지침에는 확인 번호가 그대로 적혀 있어요.
- 저장소를 비공개(Private)로 만들면 파일은 숨길 수 있어요. 다만 비공개 저장소에서 Pages를 쓰려면 GitHub 유료 요금제가 필요해요.
