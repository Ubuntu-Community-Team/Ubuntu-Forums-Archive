---
title: "Does Apple Thunderbolt display work with MacBook Pro Retina and Ubuntu?"
date: 2013-06-04
forum: Apple Hardware Users
---

### Post by RMKrug on 2013-06-04
Before falling to much in love with the 27" thunderbolt display from Apple, does it work under Ubuntu 13.04 on the MacBooc Pro Retina?

If not, are there good alternatives?

Cheers,

Rainer

---

### Post by m808 on 2013-06-13
> **RMKrug said:**
> Before falling to much in love with the 27" thunderbolt display from Apple, does it work under Ubuntu 13.04 on the MacBooc Pro Retina?

If not, are there good alternatives?

Unfortunately, no it does not. I'm using Ubuntu 13.04 on a 2011 15" MacBook (the model prior to the Retina display). The port extender features work if the monitor is plugged in while booting, but it does not work when plugged in after boot, and the display briefly works during the boot sequence, but doesn't seem to work after logging in at all.

I really love the premise of a large super hi-res monitor with embedded port extender functionality and a laptop power cord to minimize clutter.

---

### Post by ksatta1 on 2013-07-01
On Macbook Pro Retina it works atleast so that you plug it in after booting (I use it at work everyday), I have it connected to a normal lcd with a thunderbolt -> dvi adapter. Also HDMI works the same way. Not 100% sure about apple's display.

You have to have nvidia proprietary drivers installed.

EDIT: looks like Apple's displays are thunderbolt only etc, might work or might not :) Anyway thunderbolt -> dvi with non-apple display works.

---

### Post by kirankom on 2013-07-07
I have a macbook pro 15". Thunderbolt display worked after I installed the nvidia driver. It works for the most part, but I cant suspend/hibernate and resume - display doesnt come back.
I cannot plugin/unplug the monitor after booting up. Have to plug it in before bootup.

usb and ethernet work fine.

---

### Post by Vincouille on 2013-11-24
Hi all,

has the 13.10 version improved anything in the thunderbolt display support ?

---

### Post by snapstaldo on 2014-01-16
> **Vincouille said:**
> Hi all,

has the 13.10 version improved anything in the thunderbolt display support ?

No my experience with 13.10 sounds the same as kirankom's. The propriety driver works fine with thunderbolt displays if you plug in the monitor before ubuntu boots. However, strangely enough, I am able to wake up the thunderbolt display fine, but when using my laptop screen if my system goes to sleep then the display doesn't wake up and goes to this strange blurred image, and I need to hard-reset the computer. This blurry image doesn't happen if I use ubuntu's display driver but then I can't connect to my thunderbolt display at home (other external displays work fine though).

---

### Post by Umbra Diaboli on 2014-01-17
I have Apple's Home Cinema Display (the predecesor to the Thunderbolt Display). I've managed to make it work using nVidia's proprietary drivers. However, I can't make the display work using Intel's GPU.

---

