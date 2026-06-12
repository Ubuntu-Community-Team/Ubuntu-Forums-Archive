---
title: "What do i burn ubuntu as on a cd?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Snare on 2006-04-20
Ok i wanna install it, but using Nero Express 6.0, do i burn it as a bootable disk or what?

---

### Post by catlett on 2006-04-20
I haven't used Nero but you do want to create a bootable disk. So if that is an option take it. Just try to see if you can control the burn speed. You want to try to get down to at least 4x.

---

### Post by wolfee on 2006-04-20
You download the iso:
[http://www.ubuntu.com/download/](http://www.ubuntu.com/download/)

Then select copy iso image in nero. Do Not copy as a data disk it has to be an iso image or it won't work

---

### Post by aysiu on 2006-04-20
[HowTo: Burn an ISO disc image with Nero in Windows](http://www.ubuntuforums.org/showthread.php?t=111589)

---

### Post by Indiana Red on 2006-04-20
Don't mean to hijack, but I am in the same stage I think.  Have the ISO, can browse it on my XP box, and I want to install this bad boy on my hand-me-down P3-450.  I am ready to repartition as necessary etc, but what is my next step.  This CD is not bootable, is it?  I dont quite understand how to go from an ISO to getting it on a HD with no OS or one I am planning to format in the process.

---

### Post by Snare on 2006-04-20
thanks guys! i tried the tab in that link aysiu, just waiting to see if it works.

btw, whats the difference in burning it at 4x and a higher one... besides the speed?

---

### Post by catlett on 2006-04-20
You need a software program that can burn the iso image in Windows to a cd. Do you have Nero or Easy Media Creator 8. If you don't have the software go to Cnet Downloads and you can get a free trial edition. Just make sure you are "burning" an image to disk, not writing a file to disk. Then put the cd in your computer and reboot. If your computer is set up to boot from the CD Rom the process will start. Just hit enter and follow the default install. It will partition your hard drive for you. If you have problems post your own thread. Just go to the top of the page in Absolute Beg. and click on "start new thread".

---

### Post by aysiu on 2006-04-20
[QUOTE=Snare]
btw, whats the difference in burning it at 4x and a higher one... besides the speed?[/QUOTE] If you burn at a slower speed (like 4x), you're far more likely to keep the integrity of the .ISO than burning at a faster speed (like 48x).

[quote=Indiana Red]Don't mean to hijack, but I am in the same stage I think. Have the ISO, can browse it on my XP box, and I want to install this bad boy on my hand-me-down P3-450. I am ready to repartition as necessary etc, but what is my next step. This CD is not bootable, is it? I dont quite understand how to go from an ISO to getting it on a HD with no OS or one I am planning to format in the process.[/quote] I'm not sure what you mean when you say you can browse the .ISO on XP. Are you using some kind of emulator program like Qemu? .ISO's generally cannot be browsed.

In any case, you don't need Nero or Easy CD Creator if you don't have them. There's a free CD burning program called [CDBurnerXP](http://www.cdburnerxp.se/help/english/burniso) that you can use.

Once burnt as a disk image on to a blank CD, the CD itself can be booted from as long as you set the BIOS to boot from CD first (as opposed to from hard drive first).

---

### Post by catlett on 2006-04-20
The slower burn speed will just give you a better copy of the image. If your burning a movie and a few frames flutter who cares. But if your installing an operating system and something "flutters" from a bad spot in the copy it could ruin your whole install. The slower the better the reproduction. High speeds are there to cut time down when buring 4gig movies and such. People would rather burn their movie faster than have a 100% perfect burn.

---

### Post by Mustard on 2006-04-20
[QUOTE=Indiana Red]Don't mean to hijack, but I am in the same stage I think.  Have the ISO, can browse it on my XP box, and I want to install this bad boy on my hand-me-down P3-450.  I am ready to repartition as necessary etc, but what is my next step.  This CD is not bootable, is it?  I dont quite understand how to go from an ISO to getting it on a HD with no OS or one I am planning to format in the process.[/QUOTE]

Burning the ISO image to a CD creates a bootable disk.  You put the CD in the CD drive, reboot the computer, check you BIOS settings to make sure its looking for a bootable CD first (before it looks for a bootable hard drive), and the CD loads the installer.

---

### Post by aysiu on 2006-04-20
[QUOTE=catlett]
Sorry to bump into your post. As always I defer to Aysiu.[/QUOTE] Please don't. I'm starting to feel like that moment in *Fight Club* when Edward Norton finally realizes... uh, I guess I shouldn't spoil it. But when everyone keeps calling him *Sir*, and he's not comfortable with that.

---

### Post by Ian Maxwell on 2006-04-20
The image you download is already of a bootable CD, so options like "make this CD bootable" are not necessary and in fact will write different, incorrect boot information to the CD.

I think Nero has an option called "burn image" or something similar. This option probably won't ask you whether you want to make the CD bootable, as that's supposed to be (and is) covered by the image itself.

---

### Post by Snare on 2006-04-20
thanks guys! got it working and lovin it!

---

