---
title: "install oracle in ubuntu 9.10"
date: 2010-10-04
forum: Bangalore Team
---

### Post by snmn77 on 2010-10-04
i have installed ubuntu 9.10....i want to use oracle in the terminal....when i use the command --> sqlplus ,it is showing command not found....what is the solution..??

---

### Post by Waappu on 2010-10-07
Hi,

You need set enviroment variables to your .bashrc

Like below. It of course depend witch Oracle database you did install
```

ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE

export PATH

```
See this Oracle XE related document
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)

---

### Post by tushargkwd on 2010-10-17
I use Ubuntu on a Virtual Windows XP Machine.

Use Virtualbox on Ubuntu and you can use Oracle on Windows.

I had used it in this way perfectly along with Apache Tomcat Server.

---

