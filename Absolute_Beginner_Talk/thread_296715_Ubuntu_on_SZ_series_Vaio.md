---
title: "Ubuntu on SZ series Vaio"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2006-11-10
Alright,I installed Ubuntu yesterday, and I love it. It's fast, and I love the GUI. Anyway, alomst everything is perfect, but I miss a few things from Windows:

Powersavings (I heard that I need to install SpeedStepper, although I have no idea how to do this... I tried.)
Dual-Core
The Stamina/Speed switch. (Currently, I am stuck using the Intel integrated chip, but I would like to be able to switch between the two... or at least be able to use the nVidia GeForce 7400 card because when trying to play Sauerbraten I noticed that my FPS was 1!)
Built in MotionEye camera/mic (I read that this is still under development, so I can wait.)

I know that there are other posts regarding these issues, and I have read them, and tried a few of them. However, after doing what they instruct, nothing has changed...

Could someone please help me?

---

### Post by guitarist549 on 2006-11-10
Bleh, does anyone know how to fix these?

---

### Post by thumper on 2006-11-27
check out [http://avilella.googlepages.com/vaiosz](http://avilella.googlepages.com/vaiosz).  Especially the scripts for switching xorg.conf files based on detected graphics cards.  This works well for me.

However, I can't get edgy to boot the generic kernel.  Perhaps this has been fixed in an update recently.  I haven't had time to check as I have been shifting to a new country.

Camera has no linux drivers.  A petition will soon be (or has already) sent to Ricoh (who built the camera) to try and get some support.

Mic works but have to use alsamixer to turn up the volume on it.

I can't get suspend/resume working yet for edgy.  I had it working on dapper for intel chipset not nvidia.

Wireless works well.

---

