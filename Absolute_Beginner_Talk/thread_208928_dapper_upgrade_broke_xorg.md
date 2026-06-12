---
title: "dapper upgrade broke xorg"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by cowley on 2006-07-04
hi, u had a beta dapper cd from may which i just installed on an old machine.  worked ok, got the wireless working then did the upgrade of 350 files. when i went to restart the pc the xserver wont start saying:

fatal server error 
caught signal 11. server aborting.

the ww's from the log say

xf86closeconsole: KDSETMODE failed: bad file descriptor
xf86closeconsole: VT_GETMODE failed: bad file descriptor

I have tried renewing the xorg etc and have also commented out the modules to see if this cures it.  i have downloaded the nvidia drivers and changed the xorg from nv to nvidia with no luck too.

any suggestions?

thanks

simon

---

### Post by Apple 101 on 2006-07-04
What kind of nvidia graphics card to you have?

---

### Post by cowley on 2006-07-05
hi, its a nvidia riva.  i ended up just downloading the final version of dapper and re-installing.  works ok now
thanks

simon

---

