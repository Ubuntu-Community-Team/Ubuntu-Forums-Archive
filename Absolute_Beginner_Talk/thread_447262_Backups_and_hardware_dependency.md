---
title: "Backups and hardware dependency"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by UncleB on 2007-05-17
Hi all,

I'm wondering what would happen if I untarred a backup from one PC onto a different one.

Does Ubuntu check for new hardware during boot and re-adjust or would it freak out?

I'm just thinking about how practical it is to make build images...

---

### Post by starcraft.man on 2007-05-17
Ummm, by untarred a backup you mean took a copy of the root from computer A and copied it over to computer B correct? I've heard of this actually working very well, though there could be on exception... if you have 3D drivers enabled in the back up and they are the opposite (say the image is for nvidia and comp B is ATI, matrox or intel) then you might have graphical issues. Also if you have Beryl/Compiz activated, that might pose further troubles... it would be best if neither of them were active/installed at time of the image, and you had your computer configured to use the "vesa" drivers, then I think you could move it anywhere.

I imagine that can be easily fixed though, you'd probably get shunted to console, login then run this command:

```
sudo dpkg-reconfigure xserver-xorg
```

then you can reconfigure every part of your hardware on that computer and make sure it works.

In general though yes, it will automatically detect less significant changes I think and adjust for them, its pretty smart :D

---

