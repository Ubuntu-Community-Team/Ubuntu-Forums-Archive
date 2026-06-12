---
title: "CD-Rom drive troubles."
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by itsdevivi on 2007-07-25
Please do not laugh at me, but I am a complete noob at linux/ubuntu

I am currently trying to install a new operating system windows vista

But i tried to find the location of the cd rom disk drive to open and execute the file but nothing is happening

I tried to open and close the drive and nothing happened please help it will be appreciated:confused:

---

### Post by Shazaam on 2007-07-25
First a couple of questions. What operating systems do you have installed on your pc right now? And what type is it, a laptop or a desktop pc? Do you know what hardware your pc has installed?

---

### Post by weth on 2007-07-25
hi, probably your cdrom is not mounted. In a terminal type:

```
sudo mount /media/cdrom0
```

or without the "0"...this should mount your cdrom. After the that you are ready to go...

you will probably have to reboot and at the bios settings set "boot from cdrom"

but as far as I know, windows will overwrite your existing linux installation so you'd better backup your important data on cd's before starting the dual installation. When you have installed vista you can install Ubuntu anew :)

---

### Post by Nervouswreck on 2007-07-25
I would strongly recommend that you don't use Vista at all. However if you insist on digging yourself into a hole, I'll be be glad to help. Here is step by step instructions:
1. Back up everything. (yes Weth, Windows over-writes everything, there's no way to avoid it
2. Mount your CD-ROM drive.
3. Retain support staff for a prolonged installation. (Staff should include a geek a lawyer and a cook.)
4. Schedule it all for a weekend when you have nothing to do.

I'm sorry to say I'm not trying to scare you. Vista stinks and Microsoft likes to make things hard to install for some reason. The last Millenium installation I did for a friend (she didn't want XP) took 2 friggin hours. By contrast OSX took me under 30 minutes.

---

### Post by Nervouswreck on 2007-07-30
I just thought of something. Vista usually comes on DVDs. If you have an older machine, the drive might not be equipped to read them. Of course, if your computer is that old Vista wouldn't run too well anyway.

---

### Post by sumguy231 on 2007-07-30
> 1. Back up everything. (yes Weth, Windows over-writes everything, there's no way to avoid it
Are you sure about that? If it's anything like XP, you can make a partition for it from a LiveCD, install it on said partition, and reinstall GRUB when you're done.

---

### Post by deadgobby on 2007-07-30
Vista may not even run on your system. It requires a top shelf vid card and large amounts of ram. You will loose your linux as well. MS does not like to share with any other O/S. So you may need to reinstall Ubie once you are done.
Good luck
Gobby

---

