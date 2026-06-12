---
title: "lost x -server when updating"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by zumbi77 on 2006-10-26
Tried updating to edgy today, but encountered some problems.

Couldn't get the update to work using gksudo. Used apt-get dist-upgrade instead. Ran the command twice, as suggested. Rebooted, but now I've lost the x-server. How can I restore it?

Help much appreciated.

---

### Post by taurus on 2006-10-26
Try boot into recovery mode from GRUB.  Then at the prompt, type

```
aptitude install xserver-xorg-video-all
```
Reboot and see if you can get X running again!!!

---

### Post by zumbi77 on 2006-10-26
Unfortunately this didn't work out. Any other advice?

Don't know if this info helps, but start-up seems to work ok except two error messages:

cannot enable RNG
RAID fails

---

### Post by taurus on 2006-10-26
After you ran the above command from recovery mode, reboot and see if you can configure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by zumbi77 on 2006-10-26
I get the following error message:

xserver-xorg is broken or not fully installed

---

### Post by zumbi77 on 2006-10-27
Can anyone help me with this? i'm not getting anywhere](*,)

---

