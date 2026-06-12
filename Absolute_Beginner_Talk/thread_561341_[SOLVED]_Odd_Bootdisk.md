---
title: "[SOLVED] Odd Bootdisk?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by odinlonewolf on 2007-09-27
Ok... Sorry for this seemingly dumb post, but I can't seem to get the new Fiesty disk to boot from CD.  I did some searching and have found other posts about setting the boot to CD option in bios first.  However, I'm not completely new.  I currently have breezy installed on my machine and was wanting to give Fiesty a try.

I downloaded the ISO from the "Get Ubuntu" page and burned the ISO to the disc.  (Using Nero in Windows and NOT as a data disk =)  ).    So after that I put the disk in the machine and it will not boot to it.  It instead loads to the Grub loader from my previous linux version.  I decided to check to see if the disk burned correctly so I mounted it in Linux and even stuck it in in windows.  I can see the files on the disk as if it burned correctly, but it will not boot.

I read a few of the readme files on the disk and it mentioned something about creating a boot disk from a .bin file.  Is this necessary?  Or did I just download the wrong ISO?

---

### Post by w4ett on 2007-09-27
you  have to set the 1st boot device to the CD/DVD in the bios....

---

### Post by odinlonewolf on 2007-09-27
Yes, I have done that.  The CD is set to be the first boot device.  I have tested with other bootable disks and it does boot to them.

---

### Post by w4ett on 2007-09-27
might be a bad burn then......in windows, will it boot to the FOSS menu?

---

### Post by odinlonewolf on 2007-09-27
Yeah, when I put the disc in, it autoruns and shows the menu where I can install the open source packages.

---

### Post by w4ett on 2007-09-27
If it autoruns the disk, I would have thought the burn was ok but....to be on the safe side review this tutorial and make sure you completed the required steps.

[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by odinlonewolf on 2007-09-27
I went back through and did the MD5 checksum thing and it says they are the same.

---

### Post by odinlonewolf on 2007-09-27
Ok, I put the CD in another machine and it seems to boot... hrmm.. 

So basically the machine in question will load other bootable discs, but not this linux disc
My 2nd machine booted to the linux disc just fine...
weird.

---

### Post by w4ett on 2007-09-27
Might be a hardware vs. media issue....but it is weird, as you say.

---

### Post by odinlonewolf on 2007-09-27
Well, amazingly I found the problem.

It appears after changing some more BIOS settings that i had to completely remove the hard disk from the boot list completely.  My motherboard has sata controllers and even though it had the CD as the first boot device it kept going straight to the SATA HD.

So .. label this one as fixed and chalk it up to my own stupidity.  Sorry to waste your time.

---

### Post by w4ett on 2007-09-27
No problem at all.....please mark your thread as "Solved"

---

### Post by odinlonewolf on 2007-09-27
Marked!  Again, thanks for your patience and time.  This is why I keep coming back to Ubuntu / Linux.  Despite having to be a bit more tech saavy than using Windows, in my opinion, it's worth it.

---

