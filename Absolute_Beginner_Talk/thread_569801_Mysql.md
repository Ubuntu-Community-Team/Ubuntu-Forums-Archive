---
title: "Mysql"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by jayaramk on 2007-10-07
i installed the mysql application .... now i got 2 problems with which i'm stuck.....

1. using the terminal i'm able to  login on to the MYSQL... but before i used to use the ORACLE which contains tables and so on... now i don't even remember what to do.....i created the database using 'create' and can anyone tell me what next to do.....???:(.. what about the tables which are present by default ... and how to see which tables are available???

2. i installed the mysql query browser but i'm unable to enter the sql using that.... can i even find a solution to this even???


can i find a solution to this.........

---

### Post by leg on 2007-10-07
[Start here]("http://dev.mysql.com/doc/refman/5.0/en/client-utility-programs.html"). Basically the pre existing tables are not for you to touch. After you have CREATEd a db that db has no tables. I would the enter the command "use db" so that my next commands operate on the db I just created.

Next you need to create a table in that db [this link]("http://dev.mysql.com/doc/refman/5.0/en/database-administration.html") is a good place to start for that but a basic one would be

```
CREATE TABLE newtable(id int NOT NULL, value text, primary key(id));
```Which will create a table named newtable with fields of id and value with id as the primary key.

You need to go through the documentation to get more from mysql.

---

### Post by jayaramk on 2007-10-07
now that i remember things i had donew long time agoo... now i created a database and even tables and i even inserted values into that tables...........


i still get the the error while i'm logging in from the mysql query browser application which i downloaded from the repositories..... i get the following msg when i try to enter


Could not connect to host '10.2.13.124'.
MySQL Error Nr. 2003
Can't connect to MySQL server on '10.2.13.124' (111)

Click the 'Ping' button to see if there is a networking problem.



i need a colution for this please.. thx in advance

---

### Post by AlexenderReez on 2007-10-07
and usually..default oracle provided you sql sample sample

[PHP]SQL> select * from tab;

TNAME                          TABTYPE  CLUSTERID
------------------------------ ------- ----------
REGIONS                        TABLE
COUNTRIES                      TABLE
LOCATIONS                      TABLE
DEPARTMENTS                    TABLE
JOBS                           TABLE
EMPLOYEES                      TABLE
JOB_HISTORY                    TABLE
EMP_DETAILS_VIEW               VIEW
DEMO_IMAGES                    TABLE
DEMO_USERS                     TABLE
DEMO_CUSTOMERS                 TABLE

TNAME                          TABTYPE  CLUSTERID
------------------------------ ------- ----------
DEMO_ORDERS                    TABLE
DEMO_ORDER_ITEMS               TABLE
DEMO_PRODUCT_INFO              TABLE
DEMO_STATES                    TABLE
DEMO_PAGE_HIERARCHY            TABLE
DEPT                           TABLE
EMP                            TABLE

18 rows selected.

SQL> desc departments;
 Name                                      Null?    Type
 ----------------------------------------- -------- ----------------------------
 DEPARTMENT_ID                             NOT NULL NUMBER(4)
 DEPARTMENT_NAME                           NOT NULL VARCHAR2(30)
 MANAGER_ID                                         NUMBER(6)
 LOCATION_ID                                        NUMBER(4)

SQL> 
[CENTER][RIGHT][/RIGHT][/CENTER][/PHP]

*not synchronize because just copy and paste....:KS:KS

---

### Post by AlexenderReez on 2007-10-07
> **jayaramk said:**
> now that i remember things i had donew long time agoo... now i created a database and even tables and i even inserted values into that tables...........


i still get the the error while i'm logging in from the mysql query browser application which i downloaded from the repositories..... i get the following msg when i try to enter


Could not connect to host '10.2.13.124'.
MySQL Error Nr. 2003
Can't connect to MySQL server on '10.2.13.124' (111)

Click the 'Ping' button to see if there is a networking problem.



i need a colution for this please.. thx in advance

there are 2 versions of sql (oracle)....first is client version...which you need to connect to server using internet connection .....second is you create a server in your computer...so you can easily use oracle even when you are having internet problem...so i guess you are using client version.....

---

### Post by jayaramk on 2007-10-07
in order to use the server should i make my system a server or should it have a ubuntu server edition????

---

### Post by AlexenderReez on 2007-10-07
i would recommend you to use server inside your pc...it is easier....but you need to download a big file for it....to install latest version
 (11 version...follow this -->

> [http://www.dizwell.com/prod/node/929](http://www.dizwell.com/prod/node/929)

)
for standard debian (10 version ...

> [http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

---

### Post by jayaramk on 2007-10-07
ok fine... i'll do it the next time i'm free ... thxx for ur support over here.......

---

### Post by depele on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mysql-admin/+bug/155274](https://bugs.launchpad.net/ubuntu/+source/mysql-admin/+bug/155274) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I need the remote connection thing.

some body an idea?

grtz.

Arne

---

