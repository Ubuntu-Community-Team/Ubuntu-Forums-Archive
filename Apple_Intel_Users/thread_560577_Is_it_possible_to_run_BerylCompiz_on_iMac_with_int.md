---
title: "Is it possible to run Beryl/Compiz on iMac with integrated video?"
date: 2007-09-26
forum: Apple Intel Users
---

### Post by Ubivetz on 2007-09-26
Hi all!

I have installed Linux at my colleague's iMac 17" (1440x900) (C2D 1.8Ghz, 2Gb RAM, Intel GMA graphics). I still can't run Beryl or Compiz at my iMac (C2D T7200, 1Gb RAM, Mobility RadeOn X1600), but I want to try with his iMac.

---

### Post by cyberdork33 on 2007-09-26
> **Ubivetz said:**
> Hi all!

I have installed Linux at my colleague's iMac 17" (1440x900) (C2D 1.8Ghz, 2Gb RAM, Intel GMA graphics). I still can't run Beryl or Compiz at my iMac (C2D T7200, 1Gb RAM, Mobility RadeOn X1600), but I want to try with his iMac.
Both should be capable. Intel graphics are easy. Just make sure you have 3D acceleration working and install whichever. no xgl needed. What version of Ubuntu are you using?

---

### Post by Dark Hornet on 2007-09-26
--yeah, you should be able to do this with no issues on the Intel gfx computer, but your ATI mac may have some issues, or at least require a bit more "tinkering".  Just like the previous poster said, make sure you have 3D acceleration when you are done.  You can check this by typing "glxgears" in a terminal....good luck.

---

### Post by Ubivetz on 2007-09-27
I have 3D acceleration in case of ATI video, but I'm not checked whether I have it in case of GMA.
I'm using Feisty 64 bit, my co-worker uses Feisty 32 bit.

P.S. I'm confused why Ubuntu uses i810 driver for integrated graphics,

---

### Post by cyberdork33 on 2007-09-27
> **Ubivetz said:**
> P.S. I'm confused why Ubuntu uses i810 driver for integrated graphics,

Fiesty uses that by default. I believe the updated 'intel' driver is the better choice. just change the driver line in your xorg.conf

---

