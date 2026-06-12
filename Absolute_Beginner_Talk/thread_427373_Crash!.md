---
title: "Crash!"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Dtree on 2007-04-29
Hi,
I was trying to get my left mouse button to work for backing up pages in my browser and I edited my xorg.conf
Looks like I did something wrong when saving my backup~ and so of course, my edited conf did not work and xorg will not boot. Can I save this in "Rescue"
Thanks,
Dennis

---

### Post by taurus on 2007-04-29
Boot into recovery mode from GRUB menu and just copy your backup again.

```
cp /etc/X11/<backup file> /etc/X11/xorg.conf
```
Or just edit it.

```
nano -B /etc/X11/xorg.conf
```
<Ctrl>o to save and <Ctrl>x to exit.

---

### Post by Dtree on 2007-04-29
Thanks Taurus

---

