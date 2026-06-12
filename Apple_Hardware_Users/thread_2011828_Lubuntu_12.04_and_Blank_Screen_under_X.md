---
title: "Lubuntu 12.04 and Blank Screen under X?"
date: 2012-06-27
forum: Apple Hardware Users
---

### Post by Iolo34 on 2012-06-27
I've got Lubuntu 12.04 running on a 1.67 G4 PowerBook with a Radeon 9700 graphics accelerator. Suspend and screen dimming currently works (running graphics in UMS mode, with Mesa 7.11 for accelerated graphics).  However, any attempt to shut the screen off (e.g. "sleep 1; xset dpms force off") fails.  The screen, instead, turns a light grey color and the LCD backlight otherwise remains on. Has anyone else run into this issue?

---

### Post by rsavage on 2012-06-28
The command works on my iBook (radeon mobility 9200), but the driver/module type thing that controlls my backlight may be different to yours.

Have you tried it with KMS?  There is no need to drop to UMS in lubuntu since it doesn't use opengl graphics. KMS is much better at 2D graphics (firefox scrolling) out-of-the-box.

---

### Post by Iolo34 on 2012-06-28
Suspend / Sleep does not work at all with my G4 Powerbook with KMS. As documented in the PowerPCFAQ, I had to switch to using the radeonfb / UMS mode to get it working properly. All things being equal, if I had to choose between having working Suspend / Sleep, and being able to shut off the LCD backlight, I'd want Suspend / Sleep.

---

### Post by rsavage on 2012-06-29
You can have suspend with KMS.  You just can't have suspend and 3d accelerated graphics.  Unless you run some opengl games or something there is no need to switch to UMS.  It requires you to setup a detailed xorg.conf (well it does me) to match the same performance as KMS.

---

### Post by Iolo34 on 2012-06-29
Well I do have a few apps that need opengl, and I've already written a passable xorg.conf, so KMS is a non-starter for me as I would like Suspend and accelerated graphics.  I'd admit I did not do much testing with Suspend + KMS on but I never got it to work properly.  Assuming you are correct that suspend works with KMS but no graphics accleration, the PowerPCFAQ needs to be edited accordingly.

---

