---
title: "Did a server install now can't get USB automounted"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by loupy on 2005-12-05
I did a server install of Breezy, because I wanted a minimal KDE install (using KDEbase instead of kubuntu-desktop). Now when I plug in my external USB drive (it does detect it as I see it in dmesg), it does not do the automount and show the icons on my desktop. What package(s) am I missing that are needed for the automount to work?

---

### Post by jakev383 on 2005-12-05
[QUOTE=loupy]I did a server install of Breezy, because I wanted a minimal KDE install (using KDEbase instead of kubuntu-desktop). Now when I plug in my external USB drive (it does detect it as I see it in dmesg), it does not do the automount and show the icons on my desktop. What package(s) am I missing that are needed for the automount will work?[/QUOTE]

I'd start with hotplug (package name should be just hotplug), udev daemon (udev), and usbutils (same package name).  That's all I can think of off the top of my head.

---

### Post by loupy on 2005-12-05
Unfortunately, I have all 3 of those installed and still no automount :(

---

### Post by loupy on 2005-12-05
I figured out the problem - hal was not installed.

---

