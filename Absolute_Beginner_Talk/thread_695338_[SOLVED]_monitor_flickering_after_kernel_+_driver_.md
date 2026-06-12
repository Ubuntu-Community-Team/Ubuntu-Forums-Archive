---
title: "[SOLVED] monitor flickering after kernel + driver upgrade"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by dnguyen1022 on 2008-02-12
Soo as with many users I got a new update notification at the top of my screen to upgrade my kernel.  I did so, and everything went fine except for one thing.  All of a sudden my resolution would not change back to what it originally was. 1280x768 it was at 800x600, so I decided to instal the new nvidia driver from the add/remove program manager.  After doing so i gave my laptopa quick reboot and now i wont load onto the login screen anymore.  At the point where its suppose to be a login screen it flickers a few times, and then ubuntu says something about waiting 2 minutes because something has gone bad.  It does this again and again. 2 minutes after 2 minutes.  can someone help me.

---

### Post by oedha on 2008-02-12
restart...when it stuck...press ctrl+F2
login as usual
then :==> sudo dpkg-reconfigure -phigh xserver-xorg
restart......

---

### Post by dnguyen1022 on 2008-02-13
THX it works!

---

### Post by oedha on 2008-02-13
so...is this solved....
if yes...please scroll up and click on thread tool to mark this as solved
thank you :)

---

