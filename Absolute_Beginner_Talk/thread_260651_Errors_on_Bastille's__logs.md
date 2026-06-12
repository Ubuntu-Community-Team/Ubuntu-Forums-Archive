---
title: "Errors on Bastille's  logs"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by mou7 on 2006-09-19
Hi ,

I ve installed Bastille on Ubuntu 6.06 and walk throw the interactive interface...Everything worked fine so far except some details which were not displayed ...

When i ve finished ...i do not find the file /var/log/Bastille/TODO...
I have an action log with  messages like :

 $GLOBAL_TEST{'ConfigureMiscPAM'}{'consolelogin'} is not defined, ask question.


Question Sendmail.sendmaildaemon will be skipped because of the file test

 Question PSAD.psad_config will be skipped because of the file test


and error-log file full warnings like  :

WARNING: The following line in the configuration file is invalid:
         .suidping="N"
         The line will be disregarded.

Thank you for your help

---

### Post by mou7 on 2006-09-19
Actually the real error is :

ERROR:   System is not running a stable Debian GNU/Linux version. Setting to 3.0.
ERROR: A fatal error has occured. On the following
line of Bastilles config, the specified answer does
not match the following perl regular expression.
config: ConfigureMiscPAM.consolelogin=
Regular Expression: "^Y$|^N$"
Please run the interactive portion of Bastille again
 and fix the error.

I could not figure out how to deal with it

---

