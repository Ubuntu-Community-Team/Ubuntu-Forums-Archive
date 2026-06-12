---
title: "Blank screen on forced fsck"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2008-01-08
When I boot up and there is a forced fsck (every 30 boots).  I get no indication that fsck is running. I just get a blank black screen that gives me the feeling that the system is hung. This has been happening since I upgraded to 7.10.

Does anyone know how to get fsck to display properly when it's forced on bootup?

---

### Post by jordanmthomas on 2008-01-08
Don't know if it's what you want, but if you take the splash (and probably quiet too) parameter(s) off your boot parameters in /boot/grub/menu.lst the fsck will be displayed like you'd expect, but you won't get a nice pretty usplash.

If you really want usplash for the other 29 boots, you could write a script that runs on shutdown (/etc/rc.shutdown) that gets the number of mounts left until check and modifies your menu.lst accordingly.

I can do that, but I don't know how to get how many mounts are left before a check.

---

### Post by DSn0wMan on 2008-01-08
That probably a good idea. The strange thing is that I have had usplash enabled in the past, but when fsck kicks in it just goes to the shell and displays fsck stuff. There must have been change in usplash for 7.10.

---

### Post by ubuntu-freak on 2008-01-09
I think there was a change to make the boot process even quieter as there is even less text than previous versions. 
 
Do you have startupmanager installed? It forces a very quiet boot with usplash but also lets you see some text in the lower half of usplash if you want.
 
Nathan

---

### Post by DSn0wMan on 2008-01-09
Thanks for reminding me about startup manager. That was the culprit. I had actually installed it to change the usplash, but didn't notice that it changed the "quietness" of the bootup. I adjusted the settings, and everything seems fine now.

---

### Post by ubuntu-freak on 2008-01-09
Glad you got it sorted. 
 
If you have weird shutdown issues anyone, set your bit depth to 16bits. Worked nicely for me.
 
Nathan

---

