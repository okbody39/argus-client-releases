# Argus Client — Releases

Horizon 직접 접속 전용 VDI 클라이언트의 **배포 파일 저장소**입니다. 소스 코드는 여기에 없습니다.
설치 파일은 [Releases](../../releases)에서 받습니다.

## 배포 파일

| 파일 | 용도 |
|---|---|
| `argus-client-X.Y.Z-windows-x64-setup.exe` | Windows 10/11 64비트 설치 프로그램 (시작 메뉴 · 제거 등록 · 관리자 설정) |
| `argus-client-X.Y.Z-windows-x64-portable.exe` | Windows 실행 파일 1개(설치 없이 실행) |
| `argus-client-X.Y.Z-linux-x64.tar.gz` | Linux 설치 묶음 (`.deb` + `install.sh` + `prereq/`) — Ubuntu 20.04 이상 · Debian 계열 |
| `argus-client_X.Y.Z_amd64.deb` | Linux 패키지만 |
| `argus-client-X.Y.Z-linux-x64-portable` | Linux 실행 파일 1개 |
| `SHA256SUMS` | 파일 무결성 확인용 해시 |

## Omnissa Horizon Client

Horizon Client 는 이 배포에 **포함되지 않습니다**. Omnissa 에서 받아 준비한 설치 파일을 설치 프로그램 옆 `prereq/` 폴더에 두면,
Horizon Client 가 없을 때 함께 무인 설치합니다.

## 설치

**Windows** (관리자 권한)
```
argus-client-X.Y.Z-windows-x64-setup.exe
argus-client-X.Y.Z-windows-x64-setup.exe /S /POLICY=http://<정책서버>:<포트>     # 무인 설치 + 서버 지정
```
옵션: `/POLICY=` · `/LICENSE=` · `/HORIZON=<Horizon 설치 파일>` · `/HORIZONARGS="<인자>"`(기본 `/silent /norestart`)

**Linux**
```
tar xzf argus-client-X.Y.Z-linux-x64.tar.gz && cd argus-client-X.Y.Z-linux-x64
sudo ./install.sh --policy-server http://<정책서버>:<포트>
```

설치 때 서버를 지정하지 않으면 첫 실행 때(또는 `argus-client --setup`) 정책 서버 / 라이선스 서버 주소를 묻습니다.

## 확인

```
shasum -a 256 -c SHA256SUMS
```

배포 파일은 아직 코드 서명이 없어 Windows 에서 "알 수 없는 게시자" 경고가 뜰 수 있습니다.

© Argus Client. All rights reserved.
