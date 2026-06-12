---
title: "Ubuntu won't boot"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by securitysix on 2006-11-14
I'm a newb to Ubuntu, so maybe the answer is bloody obvious, but I'm missing it.  I put in the Ubuntu CD and it boots up, then I tell it to start Ubuntu.  It seems to load everything fine, at least what it shows on the splash screen, then goes to a black screen with a solid cursor in the upper left corner of the screen.  This happens on both the 64- and 32-bit versions.

My machine is running an AMD Athlon 64 X2 3800+ Manchester in a Foxconn NF4SK8AA-8KRS motherboard with a pair of XFX PV-T43G-UDL6 GeForce 6600GT video cards in SLI, and 2 gig of DDR 400 system RAM.  This setup works fine in Windows XP, so I know my hardware is good.  What I can't figure out is, since I'm running SLI, do I have to flip the SLI card around to single card mode to get Ubuntu to boot?  I intend to install Ubuntu to my hard drive followed by installing the nVidia Linux drivers so I can get some working 3D accelleration going in Linux.  

So, do I have to flip the card around, set everything up as a single card, then turn the card back around to get both cards running?

Also, I tried to boot the 32 bit version on my laptop (Athlon XP 3000 with 1.25 gig of RAM and a GeForce 440 Go video) and got an error stating that it failed to allocate a resource to some memory address, then it gives some error about being unable to access HDC sectors 0 - 9 repeatedly until I manually kill it.  This may be because I don't have much space left on my laptop's hard drive, I haven't played with that too hard yet.  I also didn't write down the exact messages on that because I'm more concerned with getting it running on my desktop than my laptop.  If anyone has any thoughts on the laptop issue, though, I'd be happy to hear them.

---

### Post by unrealmstr on 2006-11-14
Im pretty sure that the drivers on the live CD dont support SLi

---

### Post by PPAAUULL on 2006-11-14
So the only problem with the 64 bit is the blinking cursor? That might be a display problem. Is there an error when you press alt + f1 or maybe it is f1 try both it should flip to a command line.

---

### Post by securitysix on 2006-11-14
> **PPAAUULL said:**
> So the only problem with the 64 bit is the blinking cursor? That might be a display problem. Is there an error when you press alt + f1 or maybe it is f1 try both it should flip to a command line.

Both the 64 and 32 bit versions act exactly the same when I try to run them on my desktop (64-bit CPU), blank screen with a cursor.  I'll those keyboard shortcuts to get to the desk top, and if all else fails, I'll turn off SLi on the motherboard and see if it will boot that way.  It will be tomorrow evening before I really get a chance to try the latter, but I can try the keyboard shortcuts later this evening.

Thanks.

---

### Post by securitysix on 2006-11-16
OK, so I yanked my second video card and flipped the SLi card around so I was running on a single card and Ubuntu boots fine.  It even installed fine, which I'm glad of, but it doesn't seem to have an option of how or where to install the boot loader, so the only way I'll be able to get it to boot from the hard drive until I sort that out will be to unplug my Windows drive.  I didn't feel like fighting with that last night, so I'll mess with it later.

---

