---
title: "Possible bug in postgresql-8.0 initdb UNICODE"
date: 2005-11-18
forum: Bug Reports / Support
---

### Post by mathieubill on 2005-11-18
Dear all,

I spent a  lot of time tracking a very specific bug with postgresql-8.0 on Ubuntu 5.10:

When I create a database in Unicode with a table containing Japanese katakana or hiragana and when I query a specific kana, the database matches the kana as if it were a wildard for every kana and thus returns all the kanas stored in the database.

As I have another server running on a debian unstable that do not have this bug (or feature?), I could compare precisely all the differences between the 2 versions in order to understand why I had this specific problem.

I found that the default postgresql-8.0 installation on ubuntu 5.10 inits the database with template0 and template1 with UNICODE encoding whereas the same installation on debian unstable use the default encoding which is SQL_ASCII.

I deleted the default pgdata repository and relaunched initdb in order to create a new repository from scratch and my bug disappeared.

I created an sql script file if you want to reproduce the bug. 

With the default postgresql ubuntu install, you will obtain 4 rows whereas in the debian unstable install or if you relaunch initdb from scratch, you will obtain only one row which is correct.

One message to the postgresql ubuntu package maintainers:
Please let the default templates encoding to SQL_ASCII instead of changing it to UNICODE because it creates problems afterwards.

I attach my sql file as a gz file because it is encoded in UTF-8, thus may not be displayed here in this forum.

Please do not hesitate to give me your opinion if you consider this a bug or a feature.

Mathieu

---

### Post by jdong on 2005-11-21
Please report to bugzilla.ubuntu.com -- this is not Backports related.

---

