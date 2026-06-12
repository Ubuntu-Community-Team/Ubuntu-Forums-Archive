---
title: "iMac with Radeon HD 4670 splits screen in four windows"
date: 2017-08-29
forum: Apple Hardware Users
---

### Post by andev2 on 2017-08-29
Hello everyone!

I've recently installed Linux on an old iMac late 2009 that's equiped with an ATI HD 4670/RV730.
As soon as I booted from liveUSB (Ubuntu 16.04.3 LTS)  I got the screen split into 4.
[ATTACH=CONFIG]276539[/ATTACH]
I learned the nomodeset trick and managed to install it no problem. 

So I have no problem when using nomodeset but I don't get HW acceleration, big issue.
Another big issue is that [COLOR=#333333][FONT=&quot]i get low brightness in the monitor and the /sys/class/backlight/ is empty.
[/FONT][/COLOR]
Using radeon.modeset=0 gets me the same results as nomodeset which makes me believe it's linked to the radeon OS driver, or Xorg, but I have to expertise there so I need you guys' help.

What could it be? VRAM? Resolution? GFX card firmware different? I'm lost ... halp!

---

### Post by deadflowr on 2017-08-29
*Thread moved to **Apple Hardware Users**.*

---

### Post by pteryges on 2017-08-31
Out of curiosity, what happens if you attach an external monitor to the Mini-DP port?

---

### Post by andev2 on 2017-09-06
it doesn't change anything. I have same issue. :(

---

### Post by lolow on 2018-03-24
I have the same issue. I try to tweak Xorg radeon options but no improvements. I still have the 4 split screens. Did you manage to solve the problem?

---

