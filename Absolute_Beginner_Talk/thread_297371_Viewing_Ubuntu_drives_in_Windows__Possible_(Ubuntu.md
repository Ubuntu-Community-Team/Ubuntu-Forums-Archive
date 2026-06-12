---
title: "Viewing Ubuntu drives in Windows?  Possible? (Ubuntu on it's own drive)"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Double_Supercool on 2006-11-11
I have seen a lot of threads (and answers) for the opposite, that is being able to mount Win drive in Ubuntu, but that worked no problems for me.

However, is it possible to do the reverse . . . see my Ubuntu drives/folders/files in Windows?

I have XP and Ubuntu on separate drives.  It is not a huge deal, but it could get annoying transferring files as I use some Windows Apps and some linux apps.

If only Adobe put their stuff on linux, windows would be history in my house!

---

### Post by meng on 2006-11-11
If your Ubuntu partition is type ext3, you can read it from Windows by installing fs-driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by IanGB on 2006-11-11
fs-driver seems to be for ext2 and not for 64 bits systems either.

---

### Post by Bretls on 2006-11-11
fs-driver works with ext3, it just doesn't utilize journaling. I have it installed on windows xp and have not run into any problems. I am running a 32bit system, so I have not been able to test on 64bit. Are you running 64bit windows or standard?

---

### Post by vroy on 2006-12-03
sorry I posted at a wrong thread

---

### Post by ron999 on 2006-12-03
Hi vroy

It seems that you have problems with Adobe Acrobat Reader.
It might be easiest to uninstall it and re-install it cleanly using Automatix.
In the meantime, right-click your pdf file and open using document viewer.
:cool:

---

