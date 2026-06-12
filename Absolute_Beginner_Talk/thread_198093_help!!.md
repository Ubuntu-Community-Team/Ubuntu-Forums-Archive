---
title: "help!!"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by builtthenburnt on 2006-06-16
help!
I did something really stupid!

I was running out of hard drive space and had been currently using Windows more often than Kubuntu, so I used PartionMagic to delete the partion that had kubuntu on it.. I then resized the partition that had windows and thought everything was fine...

Problem is when I turn on my computer, it attempts to load kubuntu and I can't access windows whatsoever.

Maybe re-installing Kubuntu will allow me to regain access to that one screen for dual-boot? I am trying to reinstall Kubuntu, but because I can't access Partion Magic to create a partion for it, I am wondering if it would be a really risky idea to attempt to resize it manually??

Sorry for all the stupid questions.

I just don't want to loose all of my files.

---

### Post by Jagot on 2006-06-16
If I understand it correctly, you have deleted Kubuntu.  If this is the case then you cannot get that screen back (GRUB) unless you install Kubuntu again.

GRUB has been written to your MBR so you just need to get rid of it so Windows can load again.

Just boot up the machine with your Windows disc in and when the installer starts up go to recovery mode, and when the prompt comes up, type:

```
fixmbr
```

Alternatively, if you don't have your Windows disk then you can use the FreeDOS boot disk:

[http://www.freedos.org/](http://www.freedos.org/)

This however needs a slightly different command:

```
fdisk /mbr
```

---

### Post by bruce89 on 2006-06-16
[QUOTE=builtthenburnt]help!
Maybe re-installing Kubuntu will allow me to regain access to that one screen for dual-boot? I am trying to reinstall Kubuntu, but because I can't access Partion Magic to create a partion for it, I am wondering if it would be a really risky idea to attempt to resize it manually??[/QUOTE]
Reinstalling Kubuntu will work, but you will have to use the manual partioning thing in the installer.  Partition magic is hopeless for creating ext3 partitons anyway.

---

