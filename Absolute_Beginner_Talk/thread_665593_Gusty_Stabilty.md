---
title: "Gusty Stabilty"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jpr13 on 2008-01-12
I upgraded from Feisty to Gusty.
I never ever had a crash in Feisty but its happened many times since the upgrade. The OS locks up and the only option is to do a hard reboot. During the crashes, the screen either freezes or goes grey and then pixilates like the video driver is going crazy. 
I disabled my restricted video drivers; i read that might be causing the crashes. Any advice?

                                                   Jason

---

### Post by nikoPSK on 2008-01-12
gutsy is stable. All bugs have been ironed out (not all but most) for your screen crashes I can say run this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bwhite82 on 2008-01-12
Another place to look for clues:
> 
dmesg

---

### Post by cotcot on 2008-01-12
A had a lot of freezes and got them solved by installing an older nvidia driver version (versions 9755 and 9643 are OK).

---

### Post by jpr13 on 2008-01-12
My card is ATI.....?
Same driver problems as nvidia?

---

### Post by eolson on 2008-01-12
I've got ATI in my laptop and don't have any problems.

---

### Post by nikoPSK on 2008-01-12
> **jpr13 said:**
> My card is ATI.....?
Same driver problems as nvidia?

ATI supports linux. :D

---

