---
title: "640x480 max res after installing d2 expansion cedega"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by buzzmandt on 2007-06-05
I installed diablo 2 and then d2 expansion in cedega and the screen flickered during install of d2 after it updated patches and restarted d2.....

now my screen won't go passed 640x480, in system settings/monitor & display it will only go as high as 640x480......please help me....already restarted x, didn't work, then restarted system, didn't work

---

### Post by buzzmandt on 2007-06-05
OMG I fixed it on my own......I'm diggin that I'm learning linux.......

don't know if i did the right thing but here's what i did.

```
sudo kedit /etc/X11/xorg.conf
```
then I browsed to /etc/X11/  to see if there was a backup copy of xorg.conf, there was and i opened it

there is a section called section: screen, the xorg.conf only had 640X480 as an option while the back up copy had a huge collection of screens and options, copied, pasted just that section from the backup copy to the running copy, saved, restarted X and it worked.....dang i feel good about that.....

couldn't have done without these boards to have learned so much from , again i thank everyone here

---

