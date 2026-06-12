---
title: "How to do a Re-Spin of DragonFlyBSD ?"
date: 2013-05-09
forum: Any Other OS
---

### Post by Haghiri75 on 2013-05-09
Hi All. 

I want to create customized DFly iso , but I don't know how to do it. In the docs , I can't find a guide to create ISO.

---

### Post by Haghiri75 on 2013-05-09
Can't anybody help me?

---

### Post by mips on 2013-05-09
Best bet would to try IRC or their mailing lists [http://www.dragonflybsd.org/mailinglists/](http://www.dragonflybsd.org/mailinglists/)

EDIT: From IRC

> <JustinS> mips: the Makefile in /usr/src/nrelease is used to build a release image
<JustinS> so if you change that file to add/remove packages and so on, you can then run it and make a custom image
<JustinS> you'll need to have a passing familiarity with makefiles
<swildner> it can also be overridden on the make line
<swildner> release(7) manpage has the variables and so on


---

### Post by Haghiri75 on 2013-05-09
Thanks Mips.

---

