---
title: "[SOLVED] open office 2.3 problems"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by just learning on 2007-11-25
I am using gutsy gibbon, I rarely use open office but when i do i would like it to work.
My problem is that no matter what component of office i am in i can only input text. When i try to do anything else(print, spellcheck, etc...) it freezes, and i have to force quit.Any idea what the problem is. I uninstalled open office and reinstalled it to no avail. The version is 2.3. Thanks in advance.

---

### Post by kleo skywalker on 2007-11-25
> **just learning said:**
> I am using gutsy gibbon, I rarely use open office but when i do i would like it to work.
My problem is that no matter what component of office i am in i can only input text. When i try to do anything else(print, spellcheck, etc...) it freezes, and i have to force quit.Any idea what the problem is. I uninstalled open office and reinstalled it to no avail. The version is 2.3. Thanks in advance.

OpenOffice2.3 in Gutsy seems to be giving a lot of people trouble. It hangs often, for example. I'm looking for a solution too, and using Google Docs in the meantime.

---

### Post by FuturePilot on 2007-11-25
It's a bug. 2.3.1 should fix this
[https://bugs.launchpad.net/bugs/131526]("https://bugs.launchpad.net/bugs/131526")
In the meantime, you can use the Human theme or remove openoffice.org-gtk which are workarounds to the problem.

---

### Post by ptn107 on 2007-11-25
I've chosen to use version 2.3.0 from the OpenOffice.org website* in the meantime.  It works fine.  Link is provided below.

.deb package ~135Mb
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.0)

.rpm package ~154Mb w/ JRE
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxintelwjre&lang=en-US&version=2.3.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxintelwjre&lang=en-US&version=2.3.0)

---

### Post by FuturePilot on 2007-11-25
> **ptn107 said:**
> I've chosen to use version 2.3.0 from the OpenOffice.org website* in the meantime.  It works fine.  Link is provided below.

.deb package ~135Mb
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxinteldeb&lang=en-US&version=2.3.0)

.rpm package ~154Mb w/ JRE
[http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxintelwjre&lang=en-US&version=2.3.0](http://openoffice.bouncer.osuosl.org/?product=OpenOffice.org&os=linuxintelwjre&lang=en-US&version=2.3.0)

The official Openoffice will not fix this. It's present in the OO builds as well. This is not an Ubuntu specific bug. It's an upstream bug
[http://qa.openoffice.org/issues/show_bug.cgi?id=82608]("http://qa.openoffice.org/issues/show_bug.cgi?id=82608")

---

### Post by just learning on 2007-11-25
Thanks future pilot, the removal of gtk was perfect(kinda boring)but it works now.thanks alot.:)

---

