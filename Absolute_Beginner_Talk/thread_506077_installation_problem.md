---
title: "installation problem"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by bluezapper on 2007-07-21
Hi all,

I have some problem when I install packages not available in ubuntu repositories.

When I install the tar.gz packages with command like using ./configure and then make install they get installed in usr/local/lib and when I try to run them my link manager is unable to find the path. How do I make them install in right directory usr/lib.


I dont want to set the the path each and every time. I want to install Miktex as I  have to write a report .Previously, I used Miktex with WinEdt on my XP.


regards,

bluezapper:)

---

### Post by Koybe on 2007-07-21
It should be an option of the configure script.
Try 
```
./configure --help
```

---

### Post by Sef on 2007-07-21
Read [How to Install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by AlexenderReez on 2007-07-21
> **bluezapper said:**
> Hi all,

I have some problem when I install packages not available in ubuntu repositories.

When I install the tar.gz packages with command like using ./configure and then make install they get installed in usr/local/lib and when I try to run them my link manager is unable to find the path. How do I make them install in right directory usr/lib.


you can find you application by which command like firefox
> reez@aLeXeNdeRreEz:~$ which firefox
/usr/bin/firefox


---

