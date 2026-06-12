---
title: "sudo trouble"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by nostrada on 2006-01-01
Hi there, 

I just shot myself in the foot. I used sudo to edit /etc/passwd and changed my one and only user's UID from 1000 to 0.

Now I can not sudo anymore, it will come back with "UID 1000 does not exist in passwd file"

Before I reinstall - anything obvious I can do? I am still logged in, but don't have any terminals in root.

Thanks and Happy New Year

---

### Post by Sutekh on 2006-01-01
If you've lost sudo access, you will need to boot into a root console to change back the line in /etc/passwd.  There are 3 ways I can suggest (from the old Ubuntu Starter Guide)

[Ubuntu Guide - How to gain root user access without login?]("http://www.ubuntuguide.org/#gainrootwithoutlogin")

[Ubuntu Guide - How to use Ubuntu Installation CD, to gain root user access?]("http://www.ubuntuguide.org/#gainrootinstallcd")

[Ubuntu Guide - How to modify kernel boot-up arguments, to gain root user access?]("http://www.ubuntuguide.org/#gainrootmodifykernel")

The first link is probably easiest to accomplish.

Once you can get root access, make the changes to /etc/passwd

---

### Post by nostrada on 2006-01-01
Sutekh, many thanks for the quick and efficient help. RTFM, eh? Even more thanks to you. It worked of course. 

Cheers,
Markus

---

