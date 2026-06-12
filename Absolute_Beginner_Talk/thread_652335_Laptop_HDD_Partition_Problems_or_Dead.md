---
title: "Laptop HDD Partition Problems or Dead?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Westie2008 on 2007-12-28
I know that this forum probably isn't the best place for this, but I am stuck. I've dabbled with some live CD's in the past and thought that I'd try to convert an old NEC Versa Premium laptop into a photo frame and use the project as an introduction to linux in the process.    The laptop hasn't got network or wireless, it has a 20GB harddrive, so loading pictures was always going to be by usb or something.  Admittedly I haven't worked the details out :-)   I've got use of a DWL-G650+ wireless PCICMA card that I thought that I could probably get going under linux.  

I had installed Ubuntu onto the laptop in the past but couldn't get the wireless working.  Somewhere along the way of trying to install a newer version of Ubuntu I've either screwed up the partitions and can't find an operating system when I boot - or my HDD has failed.  I can't figure out which!

Having extremely limited knowledge of linux, I'm stuck.

However I got this much running DSL live and trying "sudo fdisk -lu"

Disk /dev/hda: 20.0GB, 20003880960 bytes
255 heads, 63 sectors/track, 3432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot    Start        End              Blocks          Id      System
/dev/hda1         16065     17880344     8932140            f     Win95 Ext'd (LBA)
/dev/hda3      17880345  1052835839   5174777747+  c    Win95 FAT32 (LBA)

Can anyone tell me what my newbie problem is, and how to fix it if it can be fixed?
Thanks in advance.

Jason

---

### Post by The Cog on 2007-12-28
That fdisk output says there is only a pair of windows partitions on there. You could try running the installer again, telling it to use the entire disk. That will wioe the existing partitions and start from scratch.

---

### Post by Westie2008 on 2007-12-28
Thanks for the suggestion.  That gives me direction.

---

### Post by Westie2008 on 2007-12-29
Solved.
Stating the obvious got me thinking about the obvious.
Since fdisk had returned results (admittedly not the expected results), the drive must be working.  And if it's working then if i rebuild the partitions then that should fix things.  I did some research and this linux newbie found rescuecd - which contained gparted.  Created myself some new partitions and everything went smoothly from there on in.

---

### Post by laidback on 2007-12-29
Gparted is also on your Ubuntu Live CD, but possibly a slightly different version. Gparted do a bootable CD too, Google for Gparted. 
Nice to read that you've rescued yourself.

---

