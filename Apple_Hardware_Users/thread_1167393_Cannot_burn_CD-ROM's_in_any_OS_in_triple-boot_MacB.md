---
title: "Cannot burn CD-ROM's in any OS in triple-boot MacBook 4,1"
date: 2009-05-22
forum: Apple Hardware Users
---

### Post by mdgill on 2009-05-22
Hello,

I have a MacBook 4,1 triple-booting Mac OS X 10.5, Windows Vista (current SP), and Ubuntu Jaunty Jackalope 9.04 with rEFIt.  Everything works that will work in all systems except I cannot get the machine to burn discs in any OS;  discs read fine, but they won't burn.  At some point, the machine would burn discs, probably after I got it dual-booting Windows, but not with all three OS's.  Now it won't burn with 2 or 3 OS's, nor with a single Mac OS reinstalled, nor with the Genius Bar tech's external HDD.  I assumed it was the optical drive, but the Apple Store Genius Bar techs replaced both the drive and the motherboard yesterday with no luck.  Their opinion is that rEFIt changed the EFI on the motherboard.  My understanding was that Mac's had no BIOS and instead used EFI on the hard drive.  Whatever, this is a long-standing problem, and I have totally reinstalled all systems several times, but no luck.

Can someone confirm that burning is possible with rEFIt?  If so, what is your configuration?

---

### Post by mdgill on 2009-05-25
UPDATE: Burning seems to be working now in Jaunty, but still not in Leopard.  I haven't tried Vista.

Please, anybody who CAN burn in Mac OS while multi-booting Ubuntu, please post.

---

### Post by cyberdork33 on 2009-05-26
rEFIt does not modify the EFI firmware. this is a common myth. You can boot without using rEFIt if you want (hold ALT on startup).

CD burning works fine from all OSs for me and always has (and yes I use rEFIt). 

In OS X, does System Profiler (Under Hardware > Disc Burning) say that your CD-ROM has burning capabilities?

---

### Post by mdgill on 2009-05-27
System Profiler does indeed say that the drive burns.  Furthermore, for some odd reason, the drive does indeed burn in both Ubuntu and Mac OS.  The only new variable is the brand of CD-R's.  Therefore, since the old drive wouldn't burn anything, and the new drive burns at least one brand of disc in two OS's, I guess this is a hardware issue afterall.  Thank you Genius Bar techs for making a monkey out of me!  lol

---

