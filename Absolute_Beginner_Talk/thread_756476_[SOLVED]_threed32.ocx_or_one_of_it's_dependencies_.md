---
title: "[SOLVED] threed32.ocx or one of it's dependencies not registered error"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by arvevans on 2008-04-15
Attempting to run AADE Filter Designer program <http://www.aade.com/filter.htm> using WINE and experiencing "Error 339, THREED32.OCX or one of it's dependencies not correctly registered " message.  

System is Ubuntu 7.10 Gnome.  

THREED32.OCX is installed in System32 directory.

I have installed and use many other WINE supported windows programs with no problem.

Any suggestions would be appreciated.

Thanks,

Arv
_._

---

### Post by arvevans on 2008-04-16
It's fixed.  :)

After much thought and research (i.e. trial and error),

 I installed THREED32.OCX into System32, then ran regsvr32 to find that I needed MFC40.dll.
MFC40.dll was installed in System and in System32 (probably didn't really need both places) only to find that I needed ActiveX installed.
ActiveX was installed and... "It Works!, It Works!".

Arv
_._

---

