---
title: "Dual boot: hal.dll missing or corrupt"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Homeschool Hacker on 2007-03-29
I installed Ubuntu to a multi-partition drive containing WindowsXP.  When I booted up, I had an option to boot to Windows.  When I chose that option, I got the following error:
"Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll
Please reinstall a copy of the above file."

A quick search brought up the following web page: [http://www.compphix.com/corrupthal.html](http://www.compphix.com/corrupthal.html)

Do you know if I follow the steps in the page if I will mess up GRUB?
If so, what should I do?

---

### Post by undertherift on 2007-03-29
I do believe that bootcfg, fixmbr, fixboot will all erase grub from your MBR.  But that's fairly easily remedy-able.


[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Homeschool Hacker on 2007-03-29
ok, I'll go ahead and try it.

Thanks!

---

### Post by dannyboy79 on 2007-03-29
bootcfg /rebuild  does not affect grub, all it's doing is rebuilding your boot.ini file which is contained within your root partition of windows xp. (c:\ drive most likely) if you do fixmbr, than yes, this will screw up grub and you'll need to decide whether you really want to use NTLDR to chainload Ubuntu or if you want to just reinstall grub. You don't need to do fixmbr YET, just follow that link you posted and see what happens. I have also attached a great site for fixing this issue if it gets worst and you end up getting ntldr is missing, it basically rebuilds your ntdetect.com, ntldr, and boot.ini files which are critical in order to get Windows to boot whether it be from NTLDR or whether it be from chainloading it using grub. Here you go. 

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

This is only if you don't have a windows xp cd, say you got a dell or gateway which only has a restore partition and no windows cd. If it works, please donate a minimum amount for the cost of the maintenance of the site.

otherwise if you have a windows cd, follow this: 

[http://www.computerhope.com/issues/ch000465.htm#b](http://www.computerhope.com/issues/ch000465.htm#b)

---

### Post by dannyboy79 on 2007-03-29
> **Homeschool Hacker said:**
> ok, I'll go ahead and try it.

Thanks!


NO NO NO, don't do that. Grub isn't missing YET. He was only posting that if you accidentally removed grub by running FIXMBR. You haven;t done that have you? Just follow your first link, then post back as to what happens.

---

### Post by undertherift on 2007-03-29
Eeeep, sorry, Dannyboy is exactly right.  I was answering the 'what should i do if i screw up question'

Work with the bootcfg to rebuild your boot.ini.  If that doesn't work, THEN go to fixmbr. 

Sorry for the confusion!

---

### Post by Homeschool Hacker on 2007-03-29
I used bootcfg to fix the boot.ini file.  After that, (to my relief) I was able to boot to both XP and Ubuntu!

Thanks  undertherift and dannyboy79!

---

### Post by dannyboy79 on 2007-03-29
AWESOME! I am sooooo glad we got it!!!!! See about changing the subject line of this thread and put "SOLVED" at the end or the begining.

---

