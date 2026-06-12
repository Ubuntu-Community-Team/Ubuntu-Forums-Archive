---
title: "Problem with dual boot installation - Windows XP is now corrupt"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by darthvivi on 2007-10-18
I just tried installing Ubuntu a few hours ago, and it did not go so well.

I have a 60GB hard drive. Windows was using about 30GB. I defragmented the hard drive in Windows then launched Ubuntu and resized my Windows partition to 80% of the hard drive.

During the install, it got stuck at 26% and gave me an error which it said was probably due to a faulty CD drive or corrupt CD. So I scanned the CD for errors on my other computer and said there was an error in one file (I probably should have checked this first).

Now when I start the computer I tried to install Ubuntu on, it just says "error loading operating system" (when it should boot Windows)

At first I thought it may have deleted the entire partition, but then I checked in Ubuntu and it *says* the Windows partition is still there. However I know of no way to boot Windows now. Is there some way for me to boot Windows at this point, or am I out of luck?

---

### Post by Pumalite on 2007-10-18
Boot from your Installation CD. (assuming is XP), hit 'r' for Recovery>FIXMBR>FIXBOOT.

---

### Post by darthvivi on 2007-10-18
I don't have a Windows XP CD for this computer, because it was already configured. However, will any Windows XP CD work?

---

### Post by Pumalite on 2007-10-18
Any XP should do it, I think (not a windblows user here). If not, use Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Duck2006 on 2007-10-18
> **darthvivi said:**
> I don't have a Windows XP CD for this computer, because it was already configured. However, will any Windows XP CD work?

Yes

---

### Post by darthvivi on 2007-10-19
Thanks, this worked, and now I also have Ubuntu installed :)

---

