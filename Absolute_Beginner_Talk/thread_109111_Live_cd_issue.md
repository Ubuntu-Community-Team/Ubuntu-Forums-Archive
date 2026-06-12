---
title: "Live cd issue"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by B.K. on 2005-12-27
i've been trying out the live cd of 5.10 for a couple of days now after a friend reccomended i try it. Most of the time it boots up into 640x400 resolution, but once it let me choose the resolution (xserver xorg), after i chose the language and keyboard setting, so i could load it @800x600. It hasn't given me that option again. is there a way to get the live cd to do this again?

Thanks
Bk

---

### Post by aysiu on 2005-12-28
Yes.
Once it boots up, press Control-Alt-F1
Type ```
sudo dpkg-reconfigure xserver-xorg
```
Then press Control-Alt-F7

---

### Post by B.K. on 2005-12-29
i tried this and it let me configure the resolution but when i get back into gnome its still at the previous resolution. is there a step i need to take to get it to update the resolution once xorg.conf is set?

thanks,
BK

---

