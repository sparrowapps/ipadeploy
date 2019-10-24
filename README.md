# 드랍박스를 이용한 adhoc 배포를 하는 경우

.ipa 파일의 링크를 얻어서
manifest.plist 파일에 링크를 넣어 줘야 한다.

이때 일반적인 dropbox 링크가 아닌 익명의 사용자가 접근 할 수 있는 링크 dl.dropboxusercontent.com으로 변경 해야 한다.

마지막으로 manifest.plist의 드랍박스 링크를 얻어 items-service://?action=download-manifest&url= 으로 링크를 걸어

웹서버에 html로 작성 해야 모바일 브라우져에서 링크로 설치 가능 하다.

# ipadeploy를 이용하여 자동으로 링크를 생성 
위 과정을 dropbox api를 이용하여 dropbox 링크를 생성 하고

링크 주소를 jq , sed 등을 이용하여 변경 한뒤 Plistbuddy를 이용하여 manifest.plist 파일에 삽입 한다.

manifest.plist 파일의 드랍박스 링크를 얻어 html tag를 최종 출력 한다.


# 필요 명령
curl , jq

brew install jq

brew install curl


# 사용방법
xcode 에서 adhoc deploy를 한다.

폴더명이 띄어 쓰기가 되어 있는 경우 오동작을 하므로 폴더명을 띄어 쓰기 없도록 한다.

ipaddeploy를 /usr/local/bin에 복사하고 실행 권한을 준다.

chmod +x ipadeploy

cp ipadeploy /usr/local/bin


adhoc 배포 경로에서 

ipadeploy filename.ipa

마지막으로 html에 입력할 TAG 가 출력 된다.