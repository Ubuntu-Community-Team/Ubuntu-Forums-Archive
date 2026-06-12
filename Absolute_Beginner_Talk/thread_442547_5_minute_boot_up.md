---
title: "5 minute boot up?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by PepeLapiu on 2007-05-13
Is this normal? It takes about 5 minutes for my system to boot up.
I should say it is a dual boot - Kubuntu and windoze vista.

When I installed Kubuntu I didn't have a net connection so it wasn't able to download updates while installing .... could that be the reason the boot up time is so long?

Thanx for your help and cheers,
Pepe Lapiu :)

---

### Post by annda on 2007-05-13
when you see the kubuntu splash screen, hit ctrl+alt+F1 to see the verbose output - see which step takes so long.

---

### Post by starcraft.man on 2007-05-13
> **PepeLapiu said:**
> Is this normal? It takes about 5 minutes for my system to boot up.
I should say it is a dual boot - Kubuntu and windoze vista.

When I installed Kubuntu I didn't have a net connection so it wasn't able to download updates while installing .... could that be the reason the boot up time is so long?

Thanx for your help and cheers,
Pepe Lapiu :)

Ummmm, no.... thats certainly not normal... I mean I have a dual boot with XP (Vista will never touch this box) and I boot Ubuntu in just about 20 seconds on average. Can I recommend using a diagnostic...

Open the terminal and type in:

```
sudo aptitude install bootchart
```

Then reboot your computer and a picture will be stored locally showing your boot process, I forget the folder its in right now and I gotta run, so someone else can kindly tell you I'm sure :)

Best of luck.

---

### Post by beorn! on 2007-05-13
try these two things...

In grub, before you boot, hit 'e' Move to the second line, hit 'e' again. Add "profile" to the end of the line, hit escape, then hit 'b'
This profiles your boot and arranged things on the drive so they can be accessed quicker. You need to do this with every new kernel you install.

Also, I got a speed boost by commenting out everything but the 'lo' lines in /etc/network/interfaces

got this from user "tschneiter". It made my boot time go from 5 min or so to less then 30 seconds...

---

