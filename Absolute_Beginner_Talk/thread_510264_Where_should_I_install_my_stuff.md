---
title: "Where should I install my stuff?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by sim085 on 2007-07-26
Hello,

Basically my question is; what is the main difference between /usr/lib and /usr/local and /user/local/lib ?

Do all this have some kind of special purpose? For example I know that the Java1.5 was automatically installed under /usr/lib/jvm. However I read on a tutorial that I should put tomcat under /usr/local (although I placed it under /usr/local/lib - did I do wrong?)

Thanks for any information regarding this folders. I do not have any clear idea what they are used for and hope I can find some help here.

Thanks and Regards,
Sim085

---

### Post by asmoore82 on 2007-07-26
/usr/lib | /usr/bin level is for distro specific data; everything in here should be 100% portable to other Ubuntu's on the same CPU architechure.

/usr/local/lib | /usr/local/bin is for machine specific data; things that have been custom compiled and may only work on that machine's CPU or hardware setup

what are you trying to install?

---

### Post by sim085 on 2007-07-26
I installed Tomcat under usr/local/lib.
However from your reply it seems that I should have installed it under usr/lib since Tomcat can be installed on different distros.

Regards,
Sim085

---

