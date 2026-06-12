---
title: "xorg.conf per user?"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-08-14
I have my xorg.conf configured for my dualscreen setup where I can move windows from 1 screen to another (xinerama). 

Is it possible to have another xorg.conf configuration for another user? I want a 1-screen/clone setup for this user and prevent windows being opened in the secondary screen which is not used by this user.

---

### Post by rdd on 2006-08-14
I don't believe this is possible. The Xserver is started before login, so there would be no way to switch it depending on who logs in. 

A dirty way would be to make two different versions of the xorg.conf with settings for dual and single head. The you could have a script that copies the right one into place. But it would mean you would have to boot the computer, switch to the console, run the appropriate script and then restart the xserver and login. 

Man this is really not pretty. 

Regards

rdd

---

### Post by lorre on 2006-08-14
Thnx (again).. Booting again is not the solution i'm looking for. Is it not possible to disable a screen (without re-booting) in a user specific startup script?

---

### Post by rdd on 2006-08-14
You wouldn't have to reboot. Just kill the Xserver, put the other xorg.conf in place and start the Xserver again.

---

### Post by lorre on 2006-08-15
> **rdd said:**
> You wouldn't have to reboot. Just kill the Xserver, put the other xorg.conf in place and start the Xserver again.

Ah, that's less disturbing but still a hack.

---

