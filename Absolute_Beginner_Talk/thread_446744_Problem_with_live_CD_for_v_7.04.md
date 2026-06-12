---
title: "Problem with live CD for v 7.04"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by oldeskule on 2007-05-17
I am an absolute Newb to Linux.  With that out of the way, here is my problem.  

I have attemtped to run a Live CD of Ubuntu v7.04 on my HP Pavillion (Celeron 2.70GHz  with 256M RAM)
As soon as the the start program runs Ubuntu zeros in on my A: drive and locks there.  Shortly thereafter I receive the following message:

Busybox v1.1.3(Debian 1:1.1.3-3Ubunut3) built in shell (ash)

/bin/sh: can't access tty: job control turned off
(initramfs) [77.004113] ata2.00
failed to set Xfermode(err-mask=0x4)

Since I am a total newbie, I would be better off trying to read Greek than understand what it meant.  Is there anyone out there who can act as translater for me?

I am so $ick of M$window$ that I really need get my box weaned from the garbage of M$ and into healthy food like Ubuntu

Thank you in advance

---

### Post by kittyhawk63 on 2007-05-17
You need to make sure that in BIOS your CD Drive is set as "first" to boot to. Have you done this? If not, that is probably your problem. Try it.

---

### Post by starcraft.man on 2007-05-17
Ok, this is easy, your having the same problem many others had with the new kernel (i even had this at beginning). [Here]("http://ubuntuforums.org/showthread.php?t=415009&highlight=control+tty") is the big topic talking about it. The problem stems from how the new kernel handles multiple drives, and in particular certain hardware. 

There are several fixes to this. I fixed it by simplifying my driver set up, basically I simply removed my second CD/DVD drive. If you have multiple HDDs or CD/DVD drives, you can remove the extras until you only have one of each and it might be fixed. If your not a hardware person and don't want to do that, the easiest and simplest solution is to use Edgy, its older kernel won't give you any trouble. Other than those two options, you can try the work around in the big topic and scan the posts for someone will similar set up to you...

Hope ya fix it, and if ya want edgy you can get it [here]("http://releases.ubuntu.com/") :) Oh and I am sympathetic of being sick of MS, so am I >.>.

Edit: I kinda assumed he had cd drive as first boot kittyhawk, if ya don't have that set do do that first.

---

### Post by oldeskule on 2007-05-17
My system boots to CD first, then as it reads the CD, it scans through my A: drive (floppy-yeah I still have one).  This is wear it locks up.  I have tried to disable the A: drive but Ubuntu is so effective that it reads it until it locks.  

I have tried to boot the Live CD in safe graphics and have checked the disc for errors.  I am so very frustrated with M$ that I am wiling to put up with these minor glitches if it gets me up and running!

Thanks for your help, I will try the suggested remedies and see if that works.

---

