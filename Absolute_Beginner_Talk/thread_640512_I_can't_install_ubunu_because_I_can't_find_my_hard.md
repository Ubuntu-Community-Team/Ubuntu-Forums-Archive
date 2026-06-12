---
title: "I can't install ubunu because I can't find my harddrive"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Cruisercommander on 2007-12-14
I'm trying to install ubuntu, but the installation program won't see my harddrive.  (PIII-600, two physical IDE drives(20 &30 gigs), 384 memory).  I also get a DMA status error.  Windows still boots fine and sees both harddrives.  Help! I can't fix what I can't install

---

### Post by Bruce M. on 2007-12-14
> **Cruisercommander said:**
> I'm trying to install ubuntu, but the installation program won't see my harddrive.  (PIII-600, two physical IDE drives(20 &30 gigs), 384 memory).  I also get a DMA status error.  Windows still boots fine and sees both harddrives.  Help! I can't fix what I can't install

Where do you have the installation program?

Is it on a CD?

If so check your BIOS to make sure your computer boots from the CD drive before the hard drives.

Insert the CD and restart your computer, the LiveCD or AlternateCD will boot into Ubuntu.

If you have the LiveCD you will boot directly into a working copy of Ubuntu.  On the desktop will be an Install Icon.  You can also check out the Applications, Places and System menus before installing to give you an idea how it will work on your system.

Note that it will be slow as you'll be working off the CD drive.
It will not bother your other OS at all.

Hope this helps.

---

### Post by LostMagix on 2007-12-14
i had the same problem, check your boot order and make sure the hard drive boots after the CD

first you may want to make sure the system itself recognizes the hard drive, i got one that no matter what i do wont show up on this system

---

### Post by dstew on 2007-12-14
When you boot the install CD, use the **ide=nodma** boot option, and you should be fine. See [this]("https://help.ubuntu.com/community/BootOptions"). The nodma option is not mentioned here, but you can see how to use boot options.

---

### Post by dwblas on 2007-12-14
> (PIII-600, two physical IDE drives(20 &30 gigs), 384 memory)You might want to try Xubuntu if Ubuntu runs too slow.  I think 500 meg is the 'reommended' minimum for a full blown Ubuntu install.  Also, I have a machine that will only boot from a CD after a three finger salute, ctr+alt+delete.  Don't have any idea why.

---

### Post by Cruisercommander on 2007-12-15
Thanks everyone, but ubuntu loads and runs just fine off the boot CD, but when I try to install, the harddrives are not "visible".  I can't select a harddrive to partition, because it isn't there.

---

