---
title: "Little help"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by absolutenewbie on 2006-08-25
We're installin Ubuntu on an old Gateway. Got the lastest version as of today. Resolution is stuck at low level which is pretty common problem from what i can gather.

Specs to the best of my knowledge:
P3 550MHz
300something ram
voodoo 3 video card or somethin

anyway weve tried a couple things from downloading 915resolution, which we later found out was only for intel cards. Then we tried 'dpkg-reconfigure xserver-xorg' and changed the settings but when we ctrl-alt-backspaced, we got weird error message which was like "xserver died" or something. Appreciate any/all help

---

### Post by LadyDoor on 2006-08-25
What was the error message?

---

### Post by thoffland on 2006-08-26
Hitting ctrl+alt+backspace kills your xserver (xorg). To get back into it, type startx or gdm... you may have to use sudo to do it: "sudo startx" or "sudo gdm". 

Hope that helps.

---

### Post by LadyDoor on 2006-08-26
I think there's a way in the GNOME system menus to change your resolution (somebody who actually uses GNOME correct me if I'm wrong)

--Door

---

