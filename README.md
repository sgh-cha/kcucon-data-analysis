# kcucon-data-analysis
kcucon 강의 과제에서 발생한 데이터 분석

[introduction]
SNS. 개인적으로는 정보화시대를 대표하는 정보화시대의 꽃이 되는 산물이라고 할 수 있다고 생각합니다. 기술의 발전 때문에 지금 빅데이터라고 할만 한 만큼의 많은 양의 데이터가 쌓였고, 이 데이터에 거의 누구나 접근할 수 있는 것이 현재의 상황인 것 같습니다. 그리고 이 빅데이터를 분석하고 데이터를 보는 일종의 통찰이 그만큼 중요해진 상홍인 것이죠.
그래서 한번 어떤 분석들을 할 수 있는지 간략하게 보여드리고자 하는 김에 이런 일종의 보고서 형식의 게시글을 작성하게 되었습니다. 어째 저의 관심사를 잘 나타내면서, 주제에 적합한 실습 예제도 공유하면서 좀 유익한 경험들이 아마도? 될 수 있지 않을까 해서 이런 글을 작성했습니다.
별다르게 다양한 데이터 분석 기술들을 소개하거나 그런 분석을 하는 것은 일단 제가 실력이 안 되기 때문에 그런 것은 못 합니다 ㅎㅎ.. 그냥 제가 할 수 있는 선에서 최대한 설명하고 소개를 드리고. 어차피 중요한 정보들은 우리가 교수님께로부터 강의에서 많이 들을 수 있을 거니까, 그리고 당장에 구글링만 적당히 해봐도 다양한 정보들을 얻을 수 있고요. 네, 이 글은 그냥 마땅히 쓸 주제도 없고 해서 그냥 쓴 글입니다 ㅎㅎㅎㅎㅎㅎ
굳이 의의를 두자면, 지금 이런 과제라는 명목으로 학생들이 소셜 네트워킹 활동을 하는 상황을 적절히 재현해 낸 상황에서 나오는 데이터들을 가지고 할 수 있는 분석? 온라인으로 사람들이 모이고 유저들의 활동 데이터가 쌓이고 할 때 어떤 것들을 우리가 볼 수 있는지 적절하게 예시했다는 것? 정도가 되겠네요.
실제 분석은 ㅎㅎ.. 제가 실력이 안 되서 아마 마감시간 내로 분석까지 해서 결과 내고 보고서처럼 작성하고 하는 것은 불가능할 것 같아서, 그냥 되게 뻔하고 잘 알려진 현상들을 예측 결과로 제시됐다고 가정하고 글을 작성했습니다. 혹시 데이터 분석 잘하시는 분이 계시면 한번 분석 돌리고 공유해주시면… ㅎㅎ… 감사히 잘 보겠습니당~
여기 환경이 파일 올리고 분석 결과를 올리고 하기에는 적합한 환경이 아닌 거 같아서, 임시로 만든 깃헙 계정 링크를 따로 올리겠습니다. 여기에 raw 데이터랑 약간의 전처리(수작업으로 함ㅠㅠㅠㅠ)를 한 데이터를 첨부했습니다.
https://github.com/sgh-cha
분석과 관련된 자세한 사항이랑, 나중에 분석해서 올릴 결과는 해당 깃헙 계정으로 올리도록 하겠습니다. 나중에… 아마도…… 아마도… 언젠가… 분석할… 거에요…? 아마도요 아마도요 아마도… 올릴 겁니다ㅎㅎㅎㅎㅎㅎㅎㅎㅎㅎ

[methods]
==텍스트 파일==
3월 31일 오후 5시 50분 정도 부터 57분까지 수작업으로 데이터를 만들었습니다. 100줄 씩 보기로 해 놓고, 목록 클릭 – ctrl+a – ctrl+c – ctrl+v 로 해서 텍스트 파일을 만들었습니다. 인코딩은 일단 유니코드랑 utf를 만들어 놓았습니다.

==네트워크==
먼저 각 학생들의 이름을 노드로 만듭니다. 여기서 동명이인 여부는 구분하지 않는 한 학생의 메인 게시글에 다른 학생이 답글이 달려 있으면, 메인 게시글 작성자 노드를 답글 작성자 노드가 가리키는 방향의 링크를 생성합니다. 그러면 모든 글을 등록한 학생들의 이름 노드들 간의 복잡한 네트워크가 구축된 것을 볼 수 있을 겁니다.

[results]
==예측==
학생 노드의 in-vertex degree 가 log-linear로 분포하여 power law를 만족하고, 네트워크가 scale-free property를 보일 것입니다. 그 밖에는 메인 게시글의 조회수에 답글의 개수가 비례하는 분포가 나타날 것이 예측되는 정도가 있겠습니다. 메인 게시글의 조회수의 분포 역시 log-linear로 분포할 것으로 예측됩니다.

[discussion & 잡설]
==log-linear? 그래서 뭐?==
이제 상황이 종료가 되면 우리들의 게시글에 대한 양적 특성을 가지고 평가를 해서 성적을 매긴다고 가정해봅시다. 조회수와 답글 개수에 “비례”하는 어떤 척도를 만들고 백분위를 매겨서 점수를 줄 겁니다. 과연 이 평가 시스템은 합리적이라 할 수 있을까요?
우리가 지금 얻은 (가상의) 결과를 가지고는 ‘아니다’라고 답을 할 것입니다. 굳이 양적 특성만으로 평가를 하겠다고 하면 log-linear로 fitting을 한 다음에 백분위로 매기는 것이 합리적일 것입니다. 이 power law를 따르는 분포; log-linear의 분포가 나타났다는 것이 의미하는 것은, 학생들이 게시글 “내용”의 “퀄리티”를 보고 답글을 단 것이기 보다는, 그냥 답글이 “먼저 많이 달려있는” 글에 답글을 달았을 가능성을 시사하는 것입니다.

간략한 예시로 보충을 하자면, 한 회사에서 연구원 100명 정도에게 각각 맛있는 아이스크림을 만들라고 지시하고, 아이스크림의 맛있는 정도로 연구의 실적을 평가하겠다는 상황을 생각해보죠. 이 맛있는 정도는 소비자가 해당 아이스크림을 사먹은 횟수에 비례해서 점수를 매기겠다고 합니다.
이제 피험자를 모집을 하고, 꾸준히 회사에 방문해 아이스크림을 사먹게 한다고 해보죠. 아마 매일 방문을 해서 한 10개 정도의 아이스크림을 맛 볼 수 있다고 하면, 100일 정도로 충분히 시간이 지난 다음에는 맛있는 정도에 따라 아이스크림을 사먹은 횟수가 비례하게 나왔을 것 같습니다.
물론 이 맛있는 정도에 사먹은 횟수가 비례한다고 가정한 것 자체도 엄밀하게 봤을 때는 문제가 있는 가정입니만, 일단 그냥 그렇다고 해보죠.
근데 이제 학교에 가서 학교 매점에 아이스크림을 공급하고 학생들이 아이스크림을 사먹은 횟수를 보려고 합니다. 이때 예상되는 일은, 앞에서 맛있는 정도에 따라 사먹은 횟수가 선형적으로 비례했다고 하더라도, 그 선형성이 깨질 것이라는 것입니다. 맛있다 라고 ‘소문난’ 아이스크림을 평소에 사먹었을 빈도보다 더 많이 사먹었을 것이라는 거죠. 직관적으로도 꽤 그럴싸한 경우입니다.

이것이 그냥 그럴싸한 “썰” 정도로 생각이 드시죠. 그런데 이 사실을 Barabasi 라는 과학자가 “증명”을 했습니다. 간단하게 비유를 해서 설명을 하면, 소비자가 제품을 구매할 확률이 사람들이 맛있다 라고 하는 빈도수에 선형적으로 비례를 할때, 제품의 판매 횟수는 log-linear의 분포를 따른다. 이것을 “수식”으로 “증명”을 한 것입니다.
