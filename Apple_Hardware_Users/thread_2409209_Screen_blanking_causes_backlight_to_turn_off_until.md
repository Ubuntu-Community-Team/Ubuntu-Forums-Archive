---
title: "Screen blanking causes backlight to turn off until reboot"
date: 2018-12-29
forum: Apple Hardware Users
---

### Post by rocdoc on 2018-12-29
Here are my specs: LUbuntu 18.04 on a Macbook Pro 2,1 (2006-2007) with radeon video driver and Intel Duo Core 2 CPU.

All systems working just fine, including suspend. However, if I set the xfce-power-manager to blank the screen after a period of time, use the screen lock or even run from the terminal "xset dpms force off" then the screen blanks but on attempted recovery the backlight never turns back on - although the image is there to be just barely seen. Brightness control keys (which work otherwise) will not increase the backlight and neither does sending a "echo 15 > /sys/class/backlight/apple_backlight/brightness" as root. 

Any suggestions greatly appreciated.

---

### Post by howefield on 2018-12-29
Thread moved to the "*Apple Hardware Users*" forum.

---

