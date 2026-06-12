---
title: "error upgrading to fiesty, now can't boot from CD-ROM"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ncumming on 2007-06-10
I tried upgrading to fiesty, and ran into the "can't access tty; job control turned off error."  After searching the forums, I decided to wipe my machine and start over... go back and install 6.10 from scratch.  Only problem is, my computer will no longer boot from the CD-ROM drive.  I checked in the BIOS, and it is set to check the CD drive first, but it doesn't... it goes straight into loading grub and eventually back to "Busy Box v.1.1.3 "....

Can anyone help?  I am totally stuck.

---

### Post by nadamsieee on 2007-06-11
Are you sure the grub you're seeing now is on your hard disk drive and not the LiveCD?

What are your hardware specs? 64-bit cpu? Do you have both PATA and SATA drives?

I successfully installed 6.06 after 7.04 gave me the "can't access tty; job control turned off error."

---

### Post by p_quarles on 2007-06-11
Sounds like it could be hardware. CD drives break too easily. 

But, yeah, it might make sense to be sure that you've completely wiped the drive. If you have a floppy drive, you should be able to boot up one of those "wipe the drive" disks.

---

### Post by doobit on 2007-06-11
> **p_quarles said:**
> Sounds like it could be hardware. CD drives break too easily. 

But, yeah, it might make sense to be sure that you've completely wiped the drive. If you have a floppy drive, you should be able to boot up one of those "wipe the drive" disks.

I agree with this. 
Sometimes you don't wipe out all of the partitions that you originally created.

---

### Post by nadamsieee on 2007-06-11
@doobit: Your avatar is classic!

@ncumming: If you can get to a command prompt, use the **sudo fdisk -l** command to determine which partitions are on your hard disk drives. You probably will want to use a 6.06 LiveCD; the "BusyBox" message suggests you are in fact booting the 6.10 or 7.04 LiveCD and it is failing.

Good luck!

---

### Post by ncumming on 2007-06-12
Thanks for all the replies.  After trying several different suggestions i narrowed it to a hardware issue - the Drive seems to be "malfunctioning."  I'm using an old Dell Cpt 500mhz celeron laptop... i found another cd drive to swap with mine and it fixed the problem - booted from the install disk first try and i've got feisty up and running.

Still a shame that the upgrade didn't work and i had to wipe my system, but that will teach me to have a backup on hand.

---

