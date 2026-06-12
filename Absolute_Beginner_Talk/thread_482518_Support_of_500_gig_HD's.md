---
title: "Support of 500 gig HD's?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by jeepfreak2002 on 2007-06-23
Real quick:

I just did a clean install of Ubuntu 7.04 on a new 500Gig Seagate SATA drive.

The updates are all crashing stating that the files are corrupted.  I reverified the integrity of the CD, and it is fine.  Can the issue be the size of the drive?

Thanks

Jeepfreak

---

### Post by jeepfreak2002 on 2007-06-23
bump

---

### Post by Macros42 on 2007-06-23
I have it installed on a system with 2 750Gb hard drives - no problem at all - so it's not the drive size.

On another note - bumping a thread after 24 minutes is a bit extreme - this isn't irc. :)

---

### Post by insane_alien on 2007-06-23
the ext3 filesystem can handle exabyte sized disks(obviouslt they would need to be in a JBOD with todays technology but it is theoretically possible. so a 500GB disk isn't even getting close to 1% of what it can handle.

it is possible that you have a bad disk(the HDD not the CD) try getting a diagnostic disk and checking the HDD.

---

### Post by az on 2007-06-23
badblocks - search a device for bad blocks


sudo badblocks -s /dev/sda1

---

### Post by jeepfreak2002 on 2007-06-23
ty - it is a brand new HD, so I do not think that the blocks are bad.

I checked the mobo BIOS and they are in date.  I already sent one of these drives back...  I have no idea what is causing this then...

Thanks - gonna switch out a SATA cable next.

---

### Post by jeepfreak2002 on 2007-06-23
I just don't get it...  everything seems to be corrupted as far as packages go.

The OS installs fine, and seems to run OK.  I go to run updates and they just crap out.  I downloaded the seagate tools disk, and the drive passed the short test.

I swapped SATA cables, and the same thing happens.

This is an AMD64 X2 running on an nVidia 570 based mobo with an nVidia 7600GT vid card, and it is just not happy at all.  (I am only running the 32 bit version of 7.04, though)

Any other ideas?  I can run mem test in the mean time.

---

