---
title: "Installing from Memory Stick"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by 40Where on 2007-07-19
I guess I have a real beginner question.  I downloaded Ubuntu and put it on a 1gb memory stick, since it wouldn't fit on a CD.  So how do I install it on my computer.  When I look at the files on the memory stick I don't see any .exe file, and nothing I try to open will go into the install mode.  Is it just that it won't work from a memory stick or what?

---

### Post by sailor2001 on 2007-07-19
check your bios and set it to start with the usb devices

---

### Post by koganinja89 on 2007-07-19
Although there is a bug with storing your files when running off of the USB Live... you can still install from your USB if you set your bios to boot from "Removable Media" or "HDD-USB" or "HDD-ZIP". and make sure it is in the boot list before anything else.

the other way to let it boot from CD is that: "in the install folder there are instructions to get a floppy to boot from then you let the CD load everything."

---

### Post by 40Where on 2007-07-23
Well I looked at the BIOS setup, and I thought it said that the Removable Media was first on the boot list, but it still didn't work.  I'm not sure what I need to do to get this to go.

---

### Post by ugm6hr on 2007-07-23
Burning the iso to USB doesn't work.

Try this:
[http://ubuntuforums.org/showpost.php?p=2754849](http://ubuntuforums.org/showpost.php?p=2754849)

But get the latest syslinux tar.gz file from:
[http://www.kernel.org/pub/linux/utils/boot/syslinux/](http://www.kernel.org/pub/linux/utils/boot/syslinux/)

---

### Post by 40Where on 2007-07-23
Well, I have Windows ME, not XP.  Will it still work?

---

### Post by ugm6hr on 2007-07-24
> **40Where said:**
> Well, I have Windows ME, not XP.  Will it still work?

Probably? Can't hurt to try...

PS: I'm intrigued by this:
> I downloaded Ubuntu and put it on a 1gb memory stick, since it wouldn't fit on a CD.
Where did you get the download from?  Ubuntu is supposed to fit on a CD (700MB).

---

### Post by 40Where on 2007-07-24
It didn't fit on a CD - 705mb

I got it from this website.

---

### Post by ugm6hr on 2007-08-03
There is another way to get this to work:

For Feisty:
[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

You should be able to run the instruction from any Linux - and the easiest is to use DSL (which can also run from USB - and theoretically even the same USB that you want to install Ubuntu from, since DSL loads into RAM from the USB, allowing you to overwrite it!): [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_a_USB_Flash_Drive)

Also - in case anyone else searches for a solution for Dapper:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ugm6hr on 2007-08-03
Just had another thought that will be a *lot* easier!

Download Xubuntu7.04 (Feisty): [http://www.xubuntu.org/get#feisty](http://www.xubuntu.org/get#feisty)

Then write this .iso to CD-R - it is a lot smaller than the full Ubuntu, and will definitely fit onto a 700MB CD (I've done it myself).

Install this, then from within Xubuntu (if you still want Ubuntu):
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
This refers to installing Gnome (Ubuntu) on Kubuntu, but the same principles apply to Xubuntu.

---

### Post by sailor2001 on 2007-08-03
ubuntu 7.04 is 689mb, or is it 698?..........if it doesn't fit on your disk there must be something wrong with the disk or you aren't downloading the image iso

---

