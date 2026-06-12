---
title: "Ubuntu will only start in GNOME Failsafe"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by GBee on 2008-02-19
I broke it i did. I was trying the ATI driver through Envy, i had done everything according to instructions, but after reboot, it just went to a black screen, tried to reboot again after 10 minutes of a black screen, nothing, tried sudo dpkg-reconfigure xserver-xgl this got my login screen back, but when i logged in, it was just an off white screen. Logged in again, and tried the GNOME Failsafe, so here i am in failsafe mode, unable to get into a normal session???

Any help, well, would be amazing!

---

### Post by superprash2003 on 2008-02-19
This has happened to me many times too!!but havent been able to figure out the root cause of the problem!!

---

### Post by kellemes on 2008-02-19
> **GBee said:**
> I broke it i did. I was trying the ATI driver through Envy, i had done everything according to instructions, but after reboot, it just went to a black screen, tried to reboot again after 10 minutes of a black screen, nothing, tried sudo dpkg-reconfigure xserver-xgl this got my login screen back, but when i logged in, it was just an off white screen. Logged in again, and tried the GNOME Failsafe, so here i am in failsafe mode, unable to get into a normal session???

Any help, well, would be amazing!


It may help to edit your /etc/X11/xorg.conf
Change the Driver-line to "vesa" in your Device-section.. Now it probably is "fglrx" or "radeon" or "ati" I guess?
This gives yo a pretty safe fallback driver for your graphiccard..
You may want to reinstall your ati-driver though..

---

