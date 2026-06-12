---
title: "how to set the envirnoment variables after installing the Oracle Database10g"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by watermark1983 on 2007-08-09
I was installing Oracle Database10g
and i type the command : sudo gedit /etc/bash/bashrc
and add :
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/ 10.2.0/server
ORACLE_OWNER=oraclexe
ORACLE_SID=XE
export ORACLE_HOME
export ORACLE_SID
export PATH=$ORACLE_HOME/bin:$PATH


but the erro message shows up : canot found the file.and canot save it.


where i could find the .bashrc
and i searched some information.some tells to add the envirnoment variables in bash_profile.
and i dont understand the relationship between the bash_profile and bashrc...


waiting for help online...............

---

### Post by watermark1983 on 2007-08-09
sorry,i mean Oracle10g express edition .......:KS


waiting for help online

---

