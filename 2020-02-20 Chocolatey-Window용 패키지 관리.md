# [Window] Chocolatey - Window용 package 관리 프로그램

## Chocolatey 란?
- Windonw 환경에서 Mac의 Homebrew, Linux의 yum, apt-get과 같은 역할을 수행하는 **NuGet 기반의 윈도우용 패키지 관리자**
- 명령 프롬프트상에서 간단한 명령어 만으로 프로그램/패키지를 설치,삭제,업데이트 가능

![ex_screenshot](./til_img/screenshot1.png)
- Chocolatey 홈페이지 - https://chocolatey.org/

---
## Chocolatey 설치하기
### 최소사양
  - Windows7+ / Windows Server 2003+
  - PwerShell v2+
  - .NET Framework 4+
> 윈도우 10 이상의 환경에선 기본적으로 모두 지원됨


- 설치하는 방법은 여러가지가 있음
  
### Powershell 관리자 권한으로 실행
- PowerShell은 명령프롬프트/cmd 보다 향상된 명령어 입력 환경
- WinKey + R 을 눌러 실행창을 연 다음 pwershell 입력   
![ex_screenshot](./til_img/screenshot2.png)
    >관리자 권한 실행: 위의 창에서 Ctrl + Shift + Enter 를 동시에 누름

![ex_screenshot](./til_img/screenshot3.png)

--> 관리자로 들어옴

---


### Choco 설치
- https://chocolatey.org/install 에 접속하여 페이지 중간쯤에 있는 명령어를 PowerShell에서 실행
![ex_screenshot](./til_img/screenshot4.png)
- 또는 아래의 명령어 복사+붙이기 하여 실행

```python
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProt
ocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadStri
ng('https://chocolatey.org/install.ps1'))
```

![ex_screenshot](./til_img/screenshot5.png)
- 설치완료
---

## 패키지 설치하기
### 패키지 검색/목록 확인
- https://chocolatey.org/packages 에서 패키지 검색 또는 cmd/PowerShell 에서 검색

![ex_screenshot](./til_img/screenshot7.png)
- Elasticsearch 찾음
- 사진 하단의  **choco install elasticsearch**명령어를 PowerShell에 입력하면 설치됨
  
- 또는 

![ex_screenshot](./til_img/screenshot6.png)
- PowerShell 에서 search 명령어로 패키지 검색    
  --> 패키지가 없는 경우도 있음
  ```python
  choco search grafana
  ```
- 이때 -y 옵션을 미리 지정해서 입력하면 설치시 사용자의 확인을 위해 입력받는 항목들에 대해 일괄적으로 모두 Y가 적용
- 이미 설치되어 있는 프로그램을 강제로 재설치 하는 경우 --force 옵션 사용
``` python
choco install -y --force grafana
```
![ex_screenshot](./til_img/screenshot9.png)
- Grafana 설치 완료
  
---

### 특정 버전 설치
- 특정 버전에 대한 설치를 원할시 패키지 이름 뒤에 -version 옵션을 사용
``` python
choco install -y --force -jdk8 -version=8.0.221
```

### 환경변수 설정
- Java, Python, MySQL, Tomcat 등과 같이 환경 변수 설정이 필요한경우 자동으로 처리된다고 합니다...? 진짜??

![ex_screenshot](./til_img/screenshot8.png)
- elasticsearch를 다운하려는 와중 이런에러가 발생했는데... 해결방안을 못찾았음.. ㅜㅜ

### 기타 명령어
- `패키지 삭제`
``` python
choco uninstall -y 패키지이름
```
- `최신버전 업데이트`
```python
choco upgrade -y 패키지이름
```
- `설치되어 있는 패키지 확인`
```python
choco list --localonly
```
- `info: 패키지에 대한 자세한 정보`
```python
choco search 패키지이름 --exact --detailed
```
 또는
```python
choco info 패키지이름
```
