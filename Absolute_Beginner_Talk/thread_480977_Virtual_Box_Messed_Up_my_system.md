---
title: "Virtual Box Messed Up my system????"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-22
I installed Virtual Box on Ubuntu Fiesty 7.04. In the process of creating new virtual image for Windows XP I think I forgot to property indicate/initialize the CD ROM to install the XP from. I clicked Start and obviously XP did not install at all. Now I have a black screen covering my wallpaper and any applications I launch. I cannot get out of it, rebooting gets me back to that black screen although I see the docks which launch apps, but they are "under". What do I do now???????????

---

### Post by Crafty Kisses on 2007-06-22
> **bagrol1 said:**
> I installed Virtual Box on Ubuntu Fiesty 7.04. In the process of creating new virtual image for Windows XP I think I forgot to property indicate/initialize the CD ROM to install the XP from. I clicked Start and obviously XP did not install at all. Now I have a black screen covering my wallpaper and any applications I launch. I cannot get out of it, rebooting gets me back to that black screen although I see the docks which launch apps, but they are "under". What do I do now???????????

You might want to try reconfiguring your X server this possibly might be the best solution:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by bagrol1 on 2007-06-22
Thanx.  I found an answer: **Kiba Dock** made it all happen - it must not like Virtual Boc.

---

