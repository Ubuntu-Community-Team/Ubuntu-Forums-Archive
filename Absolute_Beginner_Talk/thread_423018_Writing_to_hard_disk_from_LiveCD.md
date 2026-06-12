---
title: "Writing to hard disk from LiveCD?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by The Grand Falloon on 2007-04-25
Is this possible?  I managed to screw something up pretty good in my xorg.conf file.  I'm looking at my mistake right now, but i can't do much about it because i'm running from the live CD and it's write-protected.  Gonna be tough logging in as Root to get to it, too.

---

### Post by bodhi.zazen on 2007-04-25
Yea, no problem.

Say the partition you need to fix is /dev/hda1

```
sudo mount /dev/hda1 /mnt
```

The partition is now mounted at /mnt and accessible to root.

```
gksudo gedit /mnt/etc/X11/xorg.conf
```

Or better, ```
sudo cp /mnt/etc/X11/xorg.conf.backup /mnt/etc/X11/xogr.conf
```

You do have a working backup I trust :)

---

### Post by taurus on 2007-04-25
You just have to mount your / partition from the LiveCD.  Then, edit it with gksudo gedit command.  Assuming you have mounted it to /mnt/ubuntu, then

```
gksudo gedit /mnt/ubuntu/etc/X11/xorg.conf
```
Otherwise, just boot Ubuntu from the recovery mode from GRUB menu and edit it with sudo nano.

```
sudo nano -Bw /etc/X11/xorg.conf
```

---

### Post by The Grand Falloon on 2007-04-25
Got it, thanks.  You guys rule.

---

