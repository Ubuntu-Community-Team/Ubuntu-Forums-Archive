---
title: "Dual boot Windows Ubuntu need to reinstall Windows HELP!"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by ilushkin on 2007-06-03
Ububtu gurus! 
I dual boot ubuntu and windows xp. 
I need to reinstall windows but im afraid that windows will overwrite the grub record. 
Please give me an advise how not to reinstall Ubuntu and leave grub intact. 
Thank you in advance.

---

### Post by dbott67 on 2007-06-03
As far as I know, re-installing Windows will nuke grub.  You can re-install grub after installing Windows:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

_**STANDARD WARNING & DISCLAIMERS APPLY:**_ [COLOR=Red]Backup all critical data before beginning as bad things can happen.[/COLOR]

-Dave

---

### Post by rickycodie on 2007-06-03
in setup xp will see the different partitions, use 

CODE fdisk -l

or gparted to figure out which partition is windows and install on that partition. later in the install it will ask if you want to leave the other partitons in grub alone answer yes and then do this

[http://ubuntuforums.org/showthread.php?t=451028](http://ubuntuforums.org/showthread.php?t=451028)

follow only the posts about installing win after ubuntu, then this

[http://ubuntuforums.org/showthread.php?t=456819](http://ubuntuforums.org/showthread.php?t=456819)

if you follow as i said you will **_not_** kill grub.

---

### Post by ilushkin on 2007-06-03
thank you

---

