---
title: "Widescreen Resolution Issue"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by mdk7 on 2007-08-27
Hey,

Had everything working fine but I didn't want to lug my CRT to school and finally hooked Ubuntu up to my 19inch widescreen (Samsung SyncMaster941BW, using DVI).  The optimal resolution is 1440 x 900 but when I set that about an inch on both sides of the screen gets completely messed up (like mirrors almost).  I tried messing with XORG to no avail.  Any ideas?  

I have the monitor CD with the drivers but don't know if Ubuntu can even use those (it's for Windows, I assume).  

Video card is ATI Radeon 9700 Pro.

---

### Post by rzrgenesys187 on 2007-08-27
I've heard from others that checking for and downloading the latest drivers (check online since the cd won't have linux drivers) for your video card may get it to work.  Let me know how it works, I'm trying to fix the same problem i just cant find out what drivers i need since im using integrated on a laptop

---

### Post by John.Michael.Kane on 2007-08-27
> **mdk7 said:**
> Hey,

Had everything working fine but I didn't want to lug my CRT to school and finally hooked Ubuntu up to my 19inch widescreen (Samsung SyncMaster941BW, using DVI).  The optimal resolution is 1440 x 900 but when I set that about an inch on both sides of the screen gets completely messed up (like mirrors almost).  I tried messing with XORG to no avail.  Any ideas?  

I have the monitor CD with the drivers but don't know if Ubuntu can even use those (it's for Windows, I assume).  

Video card is ATI Radeon 9700 Pro.

Hers two methods that may help you.

[screen refresh rates....]("http://ubuntuforums.org/showthread.php?p=2605716#post2605716") 

[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")

Also make sure you have your lcd's manual as you will need it during the xorg editing, and make sure you have the drivers properly installed for your gpu.

---

