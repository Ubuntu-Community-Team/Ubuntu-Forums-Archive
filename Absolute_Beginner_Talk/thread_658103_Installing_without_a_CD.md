---
title: "Installing without a CD"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by phakan on 2008-01-04
Hi!

I tried to find any old posts about this problem but I couldn't find any so here we go...

I have an old computer I want to install 7.10 on so I can run it as a web server. The problem is that I though it could boot from the CD, but apparently it can't. I also seem to have misplaced the driver for the cd-player. The computer is completely empty but I do have an old windows boot floopy so I can at least start it up. Now, is there a way to install Ubuntu straight from the hard drive? I figure I could just put the hard drive in this computer (windows xp), copy the files I need from the CD, move it back to the old one, boot it and run whatever's necesarry. Is this possible, and if so what do I need to put on the hard drive? A copy of the cd or the .iso-file? If it's possible it would be great if you could explain what I need to do quite basic, because even though I've been working a bit with linux/unix systems before I haven't installed one or done a whole lot of administrating... Hope someone can help me out!

Thanks!

---

### Post by njparton on 2008-01-04
You don't need a driver to boot directly from the cd rom during start up.

Go into the BIOS, set the CD-ROM as the first boot drive, save settings, put the ubuntu CD in and restart.

Once installed, go back into the BIOS and set the hard drive as the first boot drive.

---

### Post by phakan on 2008-01-04
I can't choose to boot from my cd, that's the problem. I can only choose to boot from my floopy or from the hard drive. So I figure my two options are either to install it from the hard drive somehow or to find the drivers so I can boot the computer with the floppy, load the drivers and then install unbuntu, but since I can't seem to find the drivers I figure my only chance is to install it straight off the hard drive.

---

### Post by meindian523 on 2008-01-04
Um,you can use GMountISO.

```
sudo apt-get install gmountiso
```

It's a graphical front-end for mount which can be used to mount iso's using a similar syntax as this:

mount -someoptions /path/to/your/ISO /dev/loop0

I don't remember the exact syntax,but I've done this once and a good example is found in the mount man page.

---

### Post by meindian523 on 2008-01-04
I forgot to mention that you need a working linux(even if it's a Live CD) to use any of the above options.

---

### Post by njparton on 2008-01-04
> **phakan said:**
> I can't choose to boot from my cd, that's the problem. I can only choose to boot from my floopy or from the hard drive. So I figure my two options are either to install it from the hard drive somehow or to find the drivers so I can boot the computer with the floppy, load the drivers and then install unbuntu, but since I can't seem to find the drivers I figure my only chance is to install it straight off the hard drive.

If you're booting directly from the BIOS, drivers aren't part of the equation.

Then again, if your BIOS doesn't have a CD boot option you have no choice as you say.

---

### Post by meindian523 on 2008-01-04
I found the exact syntax:

```
sudo mount -o loop=/dev/loop0 -t iso9660 path/to/your/ISO /path/to/your/mountpoint
```

---

### Post by logos34 on 2008-01-04
phakan, 

[Smart Boot Manager floppy]("https://help.ubuntu.com/community/SmartBootManagerHowto") can help you boot from the cdrom drive

---

