---
title: "grub loading error 17"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by bobanshirl on 2006-09-23
I have dapper installed with Win xp,I thought I would install Kubuntu which appeared to go okay when I rebooted the first time all the OS were shown I scrolled down to windows and that was okay I then rebooted to try out Kubuntu and got as far as Grub Loading please wait Error 17.Dont really know what to do now,I am on another pc using XP,any help on this would be gratefully received.

---

### Post by haxer on 2006-09-23
its a problem with grub i had the same when i first installed ubuntu its simple to fix if you got your windows xp cd ?

---

### Post by xyz on 2006-09-23
I found this googling:

> 
**Grub Error 17**
root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition


Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.



---

### Post by xyz on 2006-09-23
How about booting on your XP CD and , at the prompt, type "fixmbr"
but in case Ubuntu is still there, the fix will be different.
If I understood you right, you've got nothing working at all!

---

