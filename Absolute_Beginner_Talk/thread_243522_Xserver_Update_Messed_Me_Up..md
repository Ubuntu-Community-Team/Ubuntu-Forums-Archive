---
title: "Xserver Update Messed Me Up."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by rck_hitokiri on 2006-08-25
Dont know what happened but that last update messed up my pc as i know it, cant fix my xserver. tried everything.

---

### Post by tkjacobsen on 2006-08-25
[http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)

---

### Post by ThirdWorld on 2006-08-25
> **rck_hitokiri said:**
> Dont know what happened but that last update messed up my pc as i know it, cant fix my xserver. tried everything.

you are not alone dude, i just restart my pc, x was working today, after i aplied the update recomended in this forum i restarted, now X crashed again. I followed the instructions, even downgrade xorg, but something happend and i dont know what is it

---

### Post by ThirdWorld on 2006-08-25
> **tkjacobsen said:**
> [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)

yeap i already did that, it crashed again

---

### Post by ThirdWorld on 2006-08-25
I cant fix it this thing im writing from the live CD. 

when i atempted the fix it said:

failed to load module "glcore" (loader failed,7)
no devices detected


Whats wrong??? anybody else with this problem?

---

### Post by cantormath on 2006-08-25
The problem is the version of xserver-xorg-core which causes the problem is 10.3. (version 10.4 fixes the problem)

more about this and how to fix it without reinstalling your system.
[http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
[http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)

---

### Post by ThirdWorld on 2006-08-25
> **cantormath said:**
> The problem is the version of xserver-xorg-core which causes the problem is 10.3. (version 10.4 fixes the problem)

more about this and how to fix it without reinstalling your system.
[http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue)
[http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)

i already did that twice but im getting that message and X dont start. What can it be? something wrong with my source list?

---

### Post by cantormath on 2006-08-25
> **ThirdWorld said:**
> i already did that twice but im getting that message and X dont start. What can it be? something wrong with my source list?

did you uninstall the corrupted packages before installing those packages?

---

