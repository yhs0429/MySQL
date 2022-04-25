## 데이터베이스와 DBMS

- 데이터베이스는 데이터의 집합이다
- 데이터베이스를 관리하고 운영하는 소프트웨어를  DBMS(Database Management System)라 한다
- 데이터베이스는 여러명의 사용자나 응용프로그램과 공유하고 동시에 접근 가능

- DBMS (Database Management System) 분류
  - 계층형(Hierarchical) 1960년대 시작함 , 현재는 사용안함
  - 망형(Network) 계층형을 개선하여 1970년대 등장 현재 사용안함
  - 관계형(Relational DBMS : RDBMS) 대부분의 DBMS가 RDBMS형태
    - RDBMS는 table이라는 최소 단위로 구성되어있으며 테이블은 하나의 열 과 행 으로 이루어져있음

## SQL언어

- RDBMS에서 사용되는 언어 '에스큐엘' , '시퀄' 로 읽는다

- SQL은 국제표준화기구에서 SQL에 대한 표준을 정해서 발표함

- SQL언어는 DBMS 제품마다 조금씩 다를 수 있음

  

- DQL (Data Query Language) 데이터 질의어 , 데이터 검색,출력
  -  SELETE..FROM..WHERE
- DML (Data Manapualtion Language) 데이터 조작어, 데이터 입력,수정,삭제
  - INSERT,UPDATE,DELETE
- DDL (Data Definition Language) 데이터 정의어 , 테이블 생성 삭제 ,테이블 구조 수정
  - CREATE TABLE , DROP TABLE, ALTER TABLE
- TCL (Transaction Control Language) 트랜잭션 제어 언어 , 안정적인 데이터 처리를 위한 데이터 처리 관련어
- DLC (Data Control Language) 데이터 제어 언어 , 권한 부여

```
📌4대언어 : CRUD 
C(크리에이티브) : INSERT 
U(리드):SELECT
U(업데이트):UPDATE
D(딜리트):DELETE
```

1. **DQL** (Data Query Language)

   - SELECT ~ FROM ~ WHERE

     - select 문 은 구축된 테이블에서 데이터를 가져올때 사용한다 (조회 후 결과 보여줌)

     - select 문 은 기존의 데이터가 변경되지 않는다

     - where 다음에 조건식이 나온다. 조건에 맞는 데이터를 뽑아낼 때 사용함

   ```
   use 데이터베이스_이름
   select 열_이름
   	from 테이블_이름
   	where 조건식
   =====================
   	group by 열_이름
   	having 조건식
   	order by 열_이름
   	limit 숫자
   ```

   관계연산자(>,<,>=,<=,=) , 논리연산자 (OR,AND)

```
# 관계연산자 사용
 select  mem_id, mem_name
	from  member
	where  height <= 162;
#논리연산자 사용
select mem_id, mem_name, height
  from member
  where height <= 165
    and mem_number > 6;  -- 평균키 165이상이면서 인원6명 이상 (논리연산자 AND)

select mem_id, mem_name, height
  from member
  where height <= 165
	or mem_number > 6;  -- 평균키 165이상이거나 인원6명 이상 (논리연산자 OR)
```

​		BETWEEN ~ AND

```
select mem_name,height
	from member
	where height >= 163
	  and height <= 165;  -- and를 사용해서 평균키 163~165 조회
      
select mem_name, height
	from member
	where height between 163 and 165; -- 범위값을 구할경우 between ~ and 사용가능
```

​		IN()

```
select mem_name , addr
	from member
	where addr = '경기' or addr = '전남' or addr = '경남';
	-- 를 IN을 사용하여 간결하게 작성할 수 있음
	
select mem_name , addr
	from member
	where addr in ('경기','전남','경남');
```

​		LIKE

- 특정 단어가 포함되거나 , 시작 , 끝나는 데이터를 검색할 때 사용
- 여러문자를 매칭하기 위해 %를 사용함
- 한 글자를 매칭하기 위해 _ 를 사용함

```
select *
	from member
	where mem_name like '우%';  -- 우 로 시작하는 문자검색
	
select *
	from member
	where mem_name like '__핑크';  -- 앞 __ 두글자는 상관없이 뒤에 핑크 라고 적힌 문자 검색
```

