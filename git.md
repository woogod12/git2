**Git 메뉴얼**
===
## **1. GIT 소개**
  + ### GIT 이란?
    + 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템.
  + ### SVN과 차이점
    + 로컬저장소와 원격저장소의 분리가능<br>
    -> 분산 처리, 안전한 데이터, 빠른 처리 속도
    + 스테이지 영역의 존재<br>
    -> 커밋 대상의 분리
    + 스냅샷을 이용한 버전 관리<br>
    -> 빠르고 편리한 브랜치 & 병합 기능
---
## **2. Git 시작하기**
+ ### git 설치    
  * http://msysgit.github.com/ 
  * 설치완료후 GIT 폴더로 가서 'git-bash.exe'를 실행합니다.
<<<<<<< HEAD

    ![실행화면](https://user-images.githubusercontent.com/44539773/63320215-f6b2e100-c357-11e9-8ae9-d4bdf6165574.PNG)
=======
    ![설치2](./git1/실행화면.png)
>>>>>>> 4d628122a510ff0ea3a1bb867d5beff3fbd5997b
    -> 위 화면이 실행되면 git 설치 완료입니다.

+ ### git 환경설정
  + git config 설정  
    + 사용자 설정 git을 commit할때 입력되는 사용자의 이메일과 이름 정보를 등록합니다.<br>
      ``` 
      $ git config --global user.name 'name'
      $ git config --global user.email example@gmail.com
      ```
    + 주로 사용할 텍스트 편집기를 입력합니다.

          $ git config --global core.editor (편집기이름)

    + git config 설정 확인을 통해 user.name과 email을 확인합니다.

          $ git config --list

---
## **3. Git 저장소 만들기**
  + ### git init
    + 'init 명령어는 해당 디렉토리를 git 레파지토리로 만들어 줍니다.  
    ls -al 명령어를 입력하면 .git 파일이 생성된것을 확인할 수 있습니다.
    ![init](https://user-images.githubusercontent.com/44539773/63320207-f31f5a00-c357-11e9-873c-15a4270864ea.PNG)
  + ### git clone
    + git clone 명령을 실행하면 프로젝트 히스토리를 전부 받아옵니다.   

          $ git clone (가저올 저장소 url)

---
## **4. Git 수정하고 저장소에 저장하기**

  + ### git status
    + 파일의 상태를 확인하는 명령어로 처음 실행하면 아래와 같은 메시지가 나온다.  

          $ git status
          On branch master
          nothing to commit, working directory clean

  + ### git add
    + git add 명령으로 파일을 새로 추적합니다.  

          $ git add (추적할파일)  

    + git add를 한후 git status 명령을 다시 실행하면 (추적할파일)이 Tracked 상태이면서 Staged 상태라는 것을 확인 할 수 있습니다.

          $ git status
          On branch master
          changes to be committed:
            (us "git reset HEAD ..." to unstage)

                new file: (추적할파일)

         
  + ### git commit
    + 커밋을 실행하면 변경된 파일이 HEAD에 반영됩니다.

          $ git commit -m "변경된 메시지 내용 입력"  
    + git add 명령 실행 이후에 수정한 파일까지 한번에 커밋하기 위한 명령어 
    
          $ git commit -am "커밋 메시지 내용"
 
  + ### git log
    + git log 명령을 통해 버전이 기록됨을 확인 할 수 있습니다. 
    ![gitlog](https://user-images.githubusercontent.com/44539773/63320197-e864c500-c357-11e9-8014-448bddb2e4b2.PNG)
---
## **5.Git remote 저장소**
  + ### git remote
    + 원격 저장소를 이용하기 위해 git 에게 아래 명령어로 원격 서버의 주소를 알려줍니다.

          $ git remote add origin <원격 서버 주소>
        -> 여기서 origin은 원격저장소의 별칭입니다.

  + ### git push
    + 최신 커밋 사항을 git repository에 올리기 위해서 사용하는 명령어 입니다.

          $ git push -u orgin master

        -> 여기서 -u 는 원격저장소로부터 업데이트를 받은후 push를 한다는 의미입니다.

---
## **6. Git branch**
  + ### 브랜치란?
    + 코드 전체를 복사해서 기존코드와 별개로 독립적 개발하는 것을 브랜치라고 합니다. 
  + ### git branch
    + 브랜치 이름을 생성하고 그 브랜치로 이동하는 명령어입니다.

          $ git branch (브랜치명)
          $ git checkout (브랜치명)
          $ git commit
          On branch (브랜치명)

  + ### git merge
    + 생성된 브랜치를 병합하는 명령어입니다.
    + 처음 명령어는 생성된 브랜치를 마스터(원격저장소)로 이동한것이고 두번째 명령어를 실행하면 생성된 브랜치를 마스터(원격저장소)로 합치게 됩니다. 

          $ git merge (브랜치명) master
          $ git merge master (브랜치명)
  + ### git merge conflict
    + merge중 충돌이 나는 상황을 해결하는 방법입니다. 먼저 충돌이 나는 상황을 예시로 들어보겠습니다.
      + master(기존저장소)에서 실험 txt 파일을 생성합니다. 그리고 해당파일을 적재하고 커밋합니다.
      + 새로운 브랜치를 만들어 똑같은 작업을 반복합니다. 
      + 다시 master(기존저장소)로 이동해서 실험 txt 파일을 수정하고 커밋합니다. 
      + 위 과정이 끝나면 master(기존저장소)에서 같은작업을한 브랜치를 merge 합니다.
      + 아래 문구가 나오면 merge conflict 상황이 완성된겁니다.

            Auto-merging merge/m1.txt
            CONFLICT (content): Merge conflict in merge/m1.txt
            Automatic merge failed; fix conflicts and then commit the result.


    + merge 툴을 활용하여 해결하기 때문에 (사용할) mergetool을 설정해야 합니다. 

          $ git config --global merge.tool (사용할tool이름)
          $ git config --global --add mergetool.(사용할tool이름).path "(사용할tool path)"
          $ git config --global --add mergetool.(사용할tool이름).trustExitCode false

    + 위 설정이 끝나면 master(기존저장소) 브랜치로 이동하여 아래 명령어를 입력해서 tool을 실행합니다.

          $ git mergetool

---
## **7. Git 기타명령어**
  + ### git diff 설정
    + git diff 는 커밋간의 HEAD와 워킹 디렉토리의 차이점을 보여줍니다.
    + difftool 설정을 통해 보다 쉽게 비교가 가능합니다.

          $ git config --global diff.tool (사용할tool이름)
          $ git config --global --add gitdifftool.kdiff3.path "C:\Program Files\KDiff3\kdiff3.exe"
          $ git config --global --add difftool.kdiff3.trustExitCode false
            

  + ### git commit --amend
    + 커밋을 수정할때 쓰는 명령어 입니다. 완료한 커밋을 수정하거나 커밋 메시지를 수정할때 사용합니다. 
            
          $ git commit --amend

  + ### .gitignore
    + Git 에게 무시할 파일 패턴을 추가해줍니다. 아래는 예시 명령입니다. 

          $ cat .gitignore
          *.[0a]
          *.~
      -> 첫줄은 .o나 .a 파일을 무시하라는 것이고, 둘째 줄은 ~로 끝나는 모든 파일을 무시하라는 것입니다. 
  + ### 기타 자주사용되는 명령어
    + 
      ```bash
      $ git branch 
        -> 로컬 branch 확인 
      $ git branch -r 
        -> 서버 branch 확인 
      $ git checkout -b 
        -> 브랜치명 브랜치를 만들고 바로 이동 
      $ git branch -d(D) (브랜치명) 
        -> -d(merge전)브랜치 삭제 / -D(merge된)브랜치 삭제  
      $ git stash 
        -> 임시저장 
      $ git stash pop 
        -> 임시저장한파일 불러오기 
      $ git remote -v 
        -> 원격 저장소 주소 확인
        ```
---
## **8. Tips & Etc**
  + ### 이슈해결
     + git 초기설정 오류시 전체 초기화 방법
     + git clean -i 명령어를 수행하고 c를 입력하면 전체 초기화를 실행합니다.
   ![clean](https://user-images.githubusercontent.com/44539773/63319813-4e504d00-c356-11e9-9237-f914cddc00fc.PNG)

  + ### Github 연동
    + GitHub에 로컬에서 만든 git을 저장하기 위해서는 GitHub의 계정을 만들고 저장할 repository가 필요합니다. 계정과 repository를 생성해주세요.

      ![github](https://user-images.githubusercontent.com/44539773/63319907-c4ed4a80-c356-11e9-8ecf-395f2dcc490e.PNG)
    + 생성한 GitHub repository로 로컬 git 연결을 위해 remote add 명령어를  사용합니다. 여기서 origin은 원격저장소의 별칭입니다.  

      ![gitpush](https://user-images.githubusercontent.com/44539773/63320201-ec90e280-c357-11e9-9869-6ca63a6d1aaa.PNG)
    + git push 명령어를 통해서 로컬저장소와 원격저장소를 동기화 시켜줍니다.
      완료되었으면 github의 자신이 생성한 repository에 로컬에서 생성한 파일들이 업로드 되어 있음을 확인할수 있습니다.

      ![gitre](https://user-images.githubusercontent.com/44539773/63320204-ee5aa600-c357-11e9-8909-81f0f76b4245.PNG)
--- 
  



     








