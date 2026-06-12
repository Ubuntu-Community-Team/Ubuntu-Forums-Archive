---
title: "mysql: &quot;not cleanly closed and upgrade needing tables&quot; problem"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by say2sky on 2007-12-29
I have used mysql server on my laptop with gutsy on xfs file system. I have tested on hardy version and have same output as following

> 
sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                               [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.


I google and couldn't find a clean solution. I have already do

> 
myisamchk *.MYI
myisamchk --recover *.MYI
myisamchk --safe-recover *.MYI


But unfortunately problem still there. I need your help about why and how this can be solved. Thank a lot for your help.

---

### Post by say2sky on 2007-12-30
Any one have any idea about this question. Please help me.

---

