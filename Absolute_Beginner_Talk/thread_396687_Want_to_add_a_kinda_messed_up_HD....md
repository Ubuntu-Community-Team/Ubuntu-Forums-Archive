---
title: "Want to add a kinda messed up HD..."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by herbster on 2007-03-29
I currently have Ubuntu on an IDE 40gb and have Vista on a SATA 320gb, with everything working perfectly, I dual boot etc.

But I have another IDE 40gb I'd like to use, which I messed up during an initial Ubuntu install long ago (powered off during partition :eek:). I then installed XP on it after formatting it ("in case") and it appeared to be ok but it started messing things up after a while as it was evident there are errors on it, so formatting isn't enough, I have to do a scan/fix it (like chkdsk in windows).

I'm wondering if I can plug it in and boot into Ubuntu, and format+scan/fix it from within Ubuntu and mount it and have it on the system (otherwise I'll just use chkdsk from Vista).

Thanks.

---

### Post by chalex on 2007-03-29
You should probably download the manufacturer's bootable diagnostic CD and run that to make sure that the drive isn't failing.  

chkdisk checks the NTFS file system integrity; you can't run it from Ubuntu.

---

### Post by devnulljp on 2007-03-29
Hook it up, boot the machine, do dmesg to find out where is it, unmount it and sudo fsck /dev/<device> on it.
You might need to format it first if it's really messed up or if it's ntfs

fdisk /dev/<device>

---

