---
title : startup file 설정 방법
date : 2020-08-21
categories : python
---
 
윈도우에서 주피터 노트북 실행 시 미리 실행되는 코드를 설정하는 방법에 대한 글이다.

## startup file 설정


### 프로필 파일 생성

다음 명령을 통해 프로필 파일을 생성할 수 있다.
```console
ipython profile create
```
경로를 찾을 수 없어 프로필 파일을 생성하지 못하는 경우에는 
 ```console
pip install ipython[all]
```
ipython을 설치하는 명령을 입력해 ipython을 설치한 후, 위의 명령을 다시 입력하면 프로필 파일을 생성할 수 있다.


### startup 파일 수정

```bash
 cd ~/.ipython/profile_default/startup 
`$ vi 00-first.py` 
```
첫 번째 줄에서 startup파일로 이동하고, 두 번째 줄에서 00-first.py 파일을 생성할 수 있다. <br>
두 번째 줄의 vi 명령어는 리눅스에서 사용되는 명령어로 윈도우에서 쓸 수 없었기에, 00-first.py가 생성된 디렉토리에 직접 들어가 git bash를 실행해주어 두 번째 명령을 입력했다. <br>
입력한 후에 파일을 수정하는 화면이 나오는데 다음의 코드와 같이 미리 실행할 코드를 작성해준다. 

```python
# basic
import time
import random

# data analytics
import numpy as np
import pandas as pd

# web crawling
import requests
from bs4 import BeautifulSoup

# visulazation
import matplotlib as mpl
import matplotlib.pyplot as plt
import seaborn as sns

sns.set()
```

작성을 완료한 후에는 `Esc` -> `:` -> `wq` -> `Enter`를 통해 저장 후 종료할 수 있다. <br>
이 때 `wq`와 같이 linux 및 unix에서 쓰이는 `vi 편집기 명령어`에 대한 전체적인 구조와 명령어를 정리해볼 수 있다. <br>


## vi 편집기 


### vi 편집기 구조
#### 1. 명령모드(command mode)
처음 명령어로 `vi`를 입력하면 들어갈 수 있다. <br>
방향키를 이용하여 커서를 이동할 수 있으며,  `dd` 나 `yy`로 한 줄 삭제 및 한 줄 붙여넣기, 또는 `x`로 글자 하나를 삭제할 수 있다. <br>
입력 모드에서 다시 돌아오려면 `ESC`를 누르면 된다. <br>

#### 2. 입력모드(insert mode)
명령모드에서 입력 모드로 넘어갈 때는 커서가 현재 위치한 부분에서부터 `i`를 통해서, 혹은 커서의 바로 다음 부분부터 `a`를 통해서 갈 수 있다. <br>
이 모드에서는 자유롭게 코드나 글을 작성을 할 수 있다. <br>

#### 3. 마지막 행 모드(last line mode)
마지막행 모드는 명령모드에서 `:`을 입력하면 화면 맨 밑에 입력을 할수 있는 공간이 나온다. <br>
여기서 현재까지 내가 작성한 이 내용을 저장하고 vi를 종료할 지, 그냥 종료할 지 등을 입력할 수 있다. <br>


### vi 편집기 명령어
다음 명령어를 입력 후 명령모드에서는 `Enter`를 누르지 않아도 명령이 실행되지만, 마지막 행 모드에서는 `Enter`을 눌러야 명령이 실행된다. <br>

#### 명령모드
>vi 명령어 | 동작
>:---:|:---:
> G | 파일의 끝으로 이동 
> $ | 커서가 있는 줄의 맨 뒤로 감
> o | 커서가 있는 줄의 맨 앞으로 감
> (N)dd | N 행 오려두기(ctrl + x)
> (N)yy | N 행 복사하기(ctrl + c)
> p | 현재 커서가 있는 줄 아래에 버퍼 내용 붙여넣기
> u | 방금 한 명령 취소(ctrl + z)
> i | 현재 커서 위치에 삽입(입력모드로 넘어감)
> a | 현재 커서 바로 다음 위치에 삽입(입력모드로 넘어감)
> (N)x | 커서가 위치한 곳의 글자 N개 삭제
> dx | 커서가 위치한 곳에서부터 단어 삭제(커서가 위치한 곳부터 띄어쓰기까지)

#### 마지막 행 모드 
>vi 명령어 | 동작
>:---:|:---:
>**w** | 현재 파일명으로 파일 저장. 꺼지지는 않음.
>w[파일명] | 입력한 파일명으로 파일 저장. 꺼지지는 않음.
>**q** | 저장되지 않고 vi 종료 
>q! | vi 강제 종료
>**wq** | 저장 후 종료
>wq! | 강제 저장 후 종료
>f[파일명] | 파일이름을 [파일명]으로 변경
>숫자 | 해당 라인으로 커서 이동
>$ | 파일의 맨 끝 줄로 이동
>e! | 마지막 저장 이후 모든 편집 취소
>/문자열 | 현재 커서 위치에서부터 파일 앞 쪽으로 문자열 탐색
>?문자열 | 현재 커서 위치에서부터 파일 뒤 쪽으로 문자열 탐색
>**set nu** | vi 라인 번호 출력
>set nonu | vi 라인 번호 출력 취소
