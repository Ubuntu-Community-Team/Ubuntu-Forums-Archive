---
title: "New Ubuntu User having problems with install"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by ViperPack on 2007-12-16
Well I am having installation problems with my HP Pavillion tx1000.  I am very tired of doing the same thing.  I wiped the drive of any crap that came with it and started from scratch with 3-50GB partitions.  On one partition I put WindowsXP, another I put Windows Vista, and another I TRIED TO INSTALL UBUNTU.  It keeps locking up in the install process though.  I have tried to create a linux compatible partition and a 520MB swap partition and used the correct things for both.  I can't find the hardware compatibility thing for Ubuntu.  ANY Suggestions

-- also, not computer illiterate, I'm a junior MIS student and have worked on computers my whole life.  please don't come at me with noob answers and troubleshooting questions but I am pretty new to linux, so bare with me.

---

### Post by dfreer on 2007-12-16
Have you tried using the alternate install cd? And verified that the Live CD images/burns were successful?

---

### Post by ViperPack on 2007-12-16
what is the alternate CD?  Ubuntu will start up, I just can't get it to install to my partition it locks up after it starts installing

---

### Post by thelatinist on 2007-12-16
> **ViperPack said:**
> what is the alternate CD?  Ubuntu will start up, I just can't get it to install to my partition it locks up after it starts installing

The alternate install CD is available from the download page.  It installs Ubuntu from a text-based installer which is less resource-intensive and may work better, depending on your hardware.

---

### Post by ViperPack on 2007-12-16
scratch that... it won't run correctly until I started it in the stable graphics or safe graphics mode... I remember that now, but that still doesn't explain the sudden lock up.

---

### Post by ViperPack on 2007-12-16
My hardware is a hp tx1000, it's an AMD turion 64 (can't remember the speed off the top of my head... currently in the bathroom with my macbook), it has a gig of ram, and a NVidia graphics card.

---

### Post by thelatinist on 2007-12-16
> **ViperPack said:**
> My hardware is a hp tx1000, it's an AMD turion 64 (can't remember the speed off the top of my head... currently in the bathroom with my macbook), it has a gig of ram, and a NVidia graphics card.

You won't know whether the alternate cd will work better unless you try it...

---

### Post by ViperPack on 2007-12-16
downloading it right now... will try

---

### Post by dptxp on 2007-12-16
Here is a nice guide for alternate CD

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by ViperPack on 2007-12-16
It still won't work.  I got it to install but everytime it boots it locks up.  I may be formatting the partition wrong or something.  I give it a 500MB swap space, and ex3 file system.

---

### Post by dfreer on 2007-12-17
Hmmm.. do you have an AMD processor in that HP laptop? I know some of the bigger models like the dv6000z, dv9000z have issues when booting, in particular I've worked on an HP dv6409wm. 

One solution (and this worked with the live CD as well) was to add the following line to the kernel boot options when booting:
```
noapic
```

The way to add these options:
Boot your computer, and at the GRUB menu select the ubuntu kernel (not the rescue mode) and press the letter **"e"**. Then, press down to highlight the *kernel* line, and press **"e"** again. At the end of the line, add the word **noapic** with a space between it and the last word in the line. Press **<Enter>**. Now, press the letter **"b"** to boot. 

If that doesn't work, you can add this at the end of the line and see if it works:
```
noapic irqpoll noirqdebug
```

---

