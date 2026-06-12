---
title: "error 21: no computer"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by raker t on 2007-06-30
I just installed ubuntu v 7.04 (from a CD) onto an older Toshiba laptop, with an external HD, via usb. The ubuntu is on the external HD. When I try to start/restart the computer, it only says: 

Grub loading stage 1.5

Grub loading, please wait
Error 21

I have Windows OS on the first HD, but I can't go anywhere on this computer, save the CD player. I changed the bios settings before all this, so at least I can still run a CD. 

Is it possible to uninstall Grub or anything from a CD? Any other help? (HELP!)

---

### Post by gn2 on 2007-06-30
> **raker t said:**
> I just installed ubuntu v 7.04 (from a CD) onto an older Toshiba laptop, with an external HD, via usb. The ubuntu is on the external HD. When I try to start/restart the computer, it only says: 

Grub loading stage 1.5

Grub loading, please wait
Error 21

I have Windows OS on the first HD, but I can't go anywhere on this computer, save the CD player. I changed the bios settings before all this, so at least I can still run a CD. 

Is it possible to uninstall Grub or anything from a CD? Any other help? (HELP!)

Running a second OS from a USB hard drive can be very unreliable in my experience.

I would suggest creating a dual-boot on the internal drive and use the external one for data storage.

You can repair the MBR to get windows booting again.

Have a good read of the Hermanzone link in my sig, it's a lot to get through, but is essential reading in my opinion.

I wish I had read it before I started using Ubuntu....

---

### Post by raker t on 2007-07-02
Thanks gn2 for the website info. Your site talks about installing grub with the terminal, how would I uninstall grub? Or can I? 

Am I understanding it right that grub is in a space that is normally blank? If so, uninstalling grub should at least get me back to being able to use MSwindows, right?

From that point, I'll find a different way to install Ubuntu, like partition hda. This add a hard drive is the lazy man's way,  no erasing the drive, reinstalling software, etc.

Here's another thing, probably not a big issue. Since I can only run a live CD at this point, I'm using the Ubuntu v5.04 to work with, and have a terminal. The Newer version (on the external HD is v7.04(?) Both the live and install are on one CD in the newer version, and it doesn't work well as a live CD, I think I'm at my ram limit. All that said, version 5.04 should work to do these terminal commands, right?

---

### Post by Redeyes_Gambit on 2007-07-03
Ahh yes, the joys of getting Ubuntu to work on an external drive...

Installing to a USB drive is currently *exceedingly* difficult, involving editing many files, and even then it's a cross-your-fingers operation. I agree with Gn2 in that I do not recommend it for anyone but the well-seasoned (and quite patient) Linux user. Now then, to restore your MBR and get GRUB replaced with the original Windows boot loader...

If you have XP follow these instructions:

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

If you have 98 you will need to dig up a boot floppy, boot to it, and type 

```

fdisk /mbr

```

 This might be a problem since you are on a laptop which I'm guessing doesn't have a floppy drive. If so, you may be able to use the ms-sys package available in the (7.04, don't know about earlier) repositories. I am unfamiliar with how to use ms-sys I am afraid, so you will have to get someone else to help you out there. The website for ms-sys can be viewed here:

[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

Just out of curiosity, how much RAM do you have? And, did you know that you *can* non-destructively shrink Windows partitions? You should be able to install Ubuntu on your internal hard-drive by resizing the Windows partition :-) . No muss, no fuss.

---

### Post by raker t on 2007-07-03
Redeyes: you did it! I got my computer back:D. It's a Toshiba techra. I think it's 256 ram. It came with an external floppy drive. I found that, and a Win98 boot floppy. Turns out I had 4 of the boot floppies, made by different people. I've got wall to wall computer stuff, old pen plotters, different stuff.  A guy I occaisionally do work for runs a computer recycling outfit. I find all kinds of vintage stuff there. Some of it, people hang on to for too long. For instance, I've seen stacks of brand new, unopened Win95 Cds. Guess we don't need that anymore, send it to the recycling place.  Once in a great while, I'll find something really cool. Best so far is a huge drawing digitizing pad. 

But I'm rambling. Thanks alot.

---

### Post by Redeyes_Gambit on 2007-07-04
Lol, I know the feeling. I'm not quite wall-to wall but I get my fair share of old computer parts. 20+ port switches, 350 MHz paperweights (Make good Ubuntu-based file servers though),  ancient ISA graphics cards, etc. :D

---

