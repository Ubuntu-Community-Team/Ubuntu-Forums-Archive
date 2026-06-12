---
title: "Knoppix-STD able to write in NTFS !!!"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-09
> The way I did this is actually quite trivial. In my case, I simply booted into an environment that would let me access the filesystem directly (For this I use a slightly modified version of Knoppix-STD with NTFS write support) and simply tamper with the logon screensaver. In Windows XP, this file is located at %SYSTEMROOT%\System32\logon.scr. I replaced it with a copy of cmd.exe, and then synced the disk and unmounted it. 
from the website : [http://silverstr.ufies.org/blog/archives/2004_01.html](http://silverstr.ufies.org/blog/archives/2004_01.html)
   
Is it possible to make a knoppix-std able to write in NTFS ??
How does it work ?

thanks

Greetz'

Patrick

---

### Post by earobinson on 2005-11-09
I am to understand (based off [http://www.ubuntuforums.org/showthread.php?t=88054](http://www.ubuntuforums.org/showthread.php?t=88054)) that this can be done in ubuntu also it is just very unstable at the moment.

how is this done, somone reverse-enginered the ntfs file system and wrote a program to handle it, the same way there is a program to handle fat

---

