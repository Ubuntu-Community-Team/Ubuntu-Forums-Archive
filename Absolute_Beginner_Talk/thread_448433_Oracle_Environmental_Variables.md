---
title: "Oracle Environmental Variables"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by TomFumb on 2007-05-19
Hi, first off, sorry if this is in the wrong forum, I couldn't work out what this qualified as

I've installed Oracle XE 10g on my Ubuntu laptop, and I can get sqlplus up and running
I do quite a lot of perl scripting, and I want to use the DBI to connect to Oracle. I've installed the DBI modules and the DBD driver with no problem, but my script can't connect as it complains that certain environmental variables are not set. 

The ones that I've come across so far are

ORACLE_HOME - which I've set to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin
TNS_ADMIN - I don't know what to set this to
ORACLE_BASE - I don't know what to set this to
and I'm sure that there are some others I'm missing

(why the hell doesn't the installer just set these anyway??)

Can anybody tell me what these environmental variables want to be set to? I'm sure it's system-dependent, but there must be a lot of people out there with a similar system to mine. 


Also, I have another little problem which isn't so imporant, but it would be nice to fix, why do I get 

/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh: 114: [[: not found 

when loading sqlplus?


Any help with any aspect of this would be greatly appreciated, so far googling has not helped

---

### Post by troach on 2007-05-30
SU into the Oracle user and you will find your variables should be set. If you copy it's variables to you, you are right.

A couple of things are wrong here.

ORACLE_HOME - which I've set to /usr/lib/oracle/xe/app/oracle/product/10.2.0/server 
TNS_ADMIN - Dont need this
ORACLE_BASE - /usr/lib/oracle/xe/app/oracle
and I'm sure that there are some others I'm missing

ORACLE_SID = XE

Now try it : )

---

