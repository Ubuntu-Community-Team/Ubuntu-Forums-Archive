---
title: "hard drive randomly stoped being recognised"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by onearmedpanda on 2007-09-14
i have a western digtal 80 gb hard drive i use as a slave drive to store all my music on. i had a little trouble getting it working at first, but i ended up having to edit the fstab and manually adding the drive, then it worked perfectly. it worked fine for about a month, then out of nowhere one day when i turned on my computer the hard drive was no longer recognized, it was very random; i hadn't done any work on it or messed with any system files at all during the last boot. i checked the fstab and it's all there here it is for anyone that wants to see it:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e377f895-5998-4a45-abc8-c8944adfd651 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=90249855-3f15-4042-a8fe-32cc7d8cd3ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1	/media/disk	ext3	defaults	0	0



the last one (sdb1) is the one that's not being recognised,
any help would be greatly appreciated
thank you : )

---

### Post by alienexplorers on 2007-09-14
Shouldn't you have a UUID number listed for sdb1 like you do for sda1.  blkid will give you the propper UUID.

---

### Post by peabody on 2007-09-14
An important question here is...

...does the BIOS autodetect the drive?  If the answer is no, it's probably died on you.

---

### Post by onearmedpanda on 2007-09-14
is there anyway to recovered the lost data if it died?

---

### Post by onearmedpanda on 2007-09-14
and how do i find out if the BIOS autodetects it, in the fstab i set it to automatically mount, but that would be linux right? not the BIOS?

---

### Post by Tautoa on 2007-09-14
If its dead, the data is probably long gone. Although I have heard that companies can get data off dead hard drives, they probably charge a lot for it though...
When you boot up, press whichever button takes you to setup (usually F2 or Delete, in my experience)
It should be listed in the BIOS setup somewhere. If not, the drive has probably gone to a better place... (which is odd, everyone knows that hard drives love Linux) :D

EDIT:  Also, you can use the /dev/ addess in the fstab, although the UUID is the 'right' way to do it

---

### Post by onearmedpanda on 2007-09-14
i checked and it was listed under the ide primary slave, so i guess it's not dead. any suggestions?

---

### Post by peabody on 2007-09-14
Hmm, what's the contents of dmesg in relation to /dev/sdb1 ?

---

### Post by onearmedpanda on 2007-09-15
when i typed dmesg i got this huge list and nothing looked like it pertained to the hard drive. 99% of it said usb 3-1 by it, im assuming it's either my mouse or my keyboard because those are the only two things i have connected via usb

---

### Post by peabody on 2007-09-15
Did you try a "dmesg | grep sdb" ?

---

### Post by onearmedpanda on 2007-09-16
i did that and got nothing, it just gave me a blank prompt again

---

### Post by peabody on 2007-09-16
Well then it could be as alienexplorers  said, you may have to get a UUID for it in fstab, although I'd find it strange if that were the case if it had worked before without one.

---

