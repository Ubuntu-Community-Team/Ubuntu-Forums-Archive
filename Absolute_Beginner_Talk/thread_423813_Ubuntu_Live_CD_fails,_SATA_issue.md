---
title: "Ubuntu Live CD fails, SATA issue?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by matth1j on 2007-04-26
Hi- just burnt a 7.0.4 live CD and tried to boot, but it stops early on with the Ubuntu logo and orange bar going backwards and forwards across the screen. I wondered if it might be because of my SATA drive, which is a Hitachi. Their website doesn't contain drivers, but advises going to the mtherboard website.

My board is an Abit SG95, which uses an SiS SATA chip (966). SiS do a linux driver for the 966, so I downloaded that, but you have to build (ie. make) it yourself and it doesn't compile :(

Anyone else had any joy with a similar setup? Any help gratefully appreciated.

BTW latest GParted live CD also doesn't see the SATA drive- it just sees the DVD drive.

Cheers
John

---

### Post by docshawnc on 2007-04-26
This is interesting.  I had a similar issue with the both the live CD and the alternate install.  I had (past tense) an ATA drive with a SATA adapter acting as my 1st hard drive.  It was not being recognized by either CD although every other bootable cd I tried worked fine.

I finally went rooting in the closet and found another SATA drive (maxtor) which I slapped in and it worked fine.  I had attributed it to my frugality in adapting an ATA to a SATA drive with the cheesy 20 buck connector.  Now it looks like there may be some as yet undocumented features in the boot process of the Fiesty CDs.

BTW, never had this problem with either Dapper nor Edgy

---

### Post by matth1j on 2007-04-26
Thanks docshawnc.

BTW although my user info states I'm a 5.10 user, I failed in my attempts to install that onto my previous 2 ATA disk PC (I couldn't configure GRUB correctly, and it kept killing the Windows installation. What a fun weekend that was ](*,)). This release is the first I've tried since, and the first on my current (SATA) PC.

John

---

### Post by aberry5555 on 2007-04-26
when you run the livecd there should be a list of functions, find one that says "edit boot functions" or similar and press that F button . delete the "quiet" bit at the end of the line and then boot again, and see where it falls over.

---

### Post by matth1j on 2007-04-26
Loading essential drivers...
Running /scripts/init --premount
Mounting root file system
Running /scripts/casper --premount
Insert driver CD and press ENTER (i386)

Tried it again, but this time didn't reach the "Insert diver CD...", and the orange bar wasn't moving.

BTW in case you're wondering, I tried to compile the SiS SATA driver on my linux (CentOS) work laptop.

Cheers
John

---

### Post by dislocated on 2007-04-27
I'm having the same problem. I've never had problems installing Ubuntu, but now with Feisty the installation stops - going to a black screen and freezing the computer after the orange progress bar has gone back and forth a few times.

With quiet mode taken out of the equation, this is the last line on the screen:
[   5.144000] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher

Then the CD spins for a while and finally stops altogether.

There seem to be more people with problems like this.

---

### Post by aberry5555 on 2007-04-27
ah thisll probably be why then, they might not work if compiled for the wrong kernel. try compiling on Live CD to a USB pen or something, then rebooting and using them

---

### Post by mrfilgueira on 2007-07-06
I had such an issue. The laptop freezes and couldn't start in live neither in vesa mode (safe graphics). The laptop got frozen while starting X.
I found that selecting a different video modes with F4 managed to start live without any extra parameter. Also, when starting in 1024x768x16, gnome was shown in 1280x800 as it should b (?).
I`m using Ubuntu 7.04 i386 on a Compaq Presario v6000 (video nvidia 6150). Hope this helps anybody !
BR

---

