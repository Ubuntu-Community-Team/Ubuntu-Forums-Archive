---
title: "Is there special way to install on laptops?"
date: 2013-09-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tahdas on 2013-09-25
Hi i just got my new asus zenbook UX32A-r3502h. I'm planning on installing Ubuntu on it, but im not sure how to. Do i just install regular old linux onto a usb stick and plug that in? or do i have to do something else? 

Also will everything work proberly after i install ubuntu? IE touch pad, backlit keyboard, special keys (such as volume/f8/10/11 key). Will the battery life be shorter?

Thanks,
tahdas

---

### Post by tahdas on 2013-09-25
Also how do i check to see how large my harddrive is on windows 7?

---

### Post by Bashing-om on 2013-09-25
tahdas; Hi ! 

That asus zenbook UX32A-r3502h looks to be pretty descent, should run what ever you install on it. Lots of choices !
A lot depends on and if that machine has secure boot and or UEFI enabled.
Best course of action at this time is for you to down load several differing 'buntu .iso files (check d/l validity with md5sum);
burn that .iso to disk( usb or pendrive, your choice) as an image at slowest speed,
set in bios the boot priority to 1st for the DVD (or CD, usb or whatever),
Boot up that liveDVD to "try ubuntu" mode.

See that all works as expected in that "try" mode /// and see which of several distributions you prefer above all others ( hey, there are hundreds of variations that later you will become aware of).

When you have made your choice;
in 'buntu "try ubuntu" mode -> terminal codes: (do not get scared at this, is but the simplest method to xfer knowledge)
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```
and if it turns out that the hard disk is in Windows' dynamic partitioning, DO:
```

sudo gdisk -l /dev/sda

```

And we will further advise you with recommendations to restructure the hard drive to accommodate 'buntu.

Millions do it and you can too !

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by tahdas on 2013-09-25
Is there a way i can check the hard drive on windows? I wanna make sure it has 500 gb like its supposed before doing anything on it. Also i cant find an empty usb drive.

Thanks,
tahdas

---

### Post by Bashing-om on 2013-09-25
tahdas; Hey !

I have not touched Windows since XP sp2, so can not advise directly.. I would expect that Windows has a disk utility with which to inspect that hard drive .
Else boot up 'buntu live environment and run those commands from my last post .. will give a proliferation of info in respect to the hard drives. 

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Barsoom88 on 2013-09-25
[FONT=times new roman]Hi, 
I could not install by usb so I did by burning a Ubuntu CD and it worked perfectly!
[/FONT]

---

### Post by Bashing-om on 2013-09-25
@ Barsoom88; Good contribution, great way to introduce yourself to the forum !

My way to Welcome you to the forum.

[INDENT][INDENT]open source, we are all in this together
[/INDENT][/INDENT]

---

### Post by tahdas on 2013-09-26
> **Barsoom88 said:**
> [FONT=times new roman]Hi, 
I could not install by usb so I did by burning a Ubuntu CD and it worked perfectly!
[/FONT]

On this computer?! It doesnt have a dvd drive. Anyway i plan on buying a usb thingy soon and i can check then.

---

### Post by tahdas on 2013-09-26
I have an sd card, can i use that?

---

### Post by Linuxisfast on 2013-09-28
Make a USB install with latest Ubuntu 12.04.3 LTS, you will find everything functioning including your nvidia card.

---

### Post by jeff32 on 2013-10-15
I installed ubuntu 12.04 on my K55A about a week ago from a usb stick. Go to the ubuntu download page, decide which one you want, download it, burn it or make a bootable usb then boot your device from cd or usb. Along the way you'll get the option to try it without installing or to do an install, then you'll be on your way.

Now, I'm not on a zenbook but all of my bells and whistles work f-keys/lights. Graphics are good and battery life is better than with winblows.

---

