---
title: "How can I tell if my raid/fakeraid is working correctly?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by b0b138 on 2008-04-15
In gparted, it shows /dev/sda (which has my xp, ubuntu, and swap partitions) and its mount point is /media/sdc1.  /dev/sdb is NOT mounted and has a triangle/exclamation icon. /dev/sdc has 2 mountpoints, /media/sda1, /media/sdb1

/dev/sdb and /dev/sdc are mirrored (under xp anyways) :confused:

---

### Post by b0b138 on 2008-04-15
bump

---

### Post by umattu on 2008-04-15
If your drives are in a RAID array in XP that in no way means that the RAID will be used for ubuntu. 

Did you install ubuntu using RAID?

If so was it software RAID (used the ubuntu installer to setup the RAID)
or is it hardware?

If it is software RAID setup by ubuntu you can check the array with this command:

sudo mdadm --detail /dev/md0 

the /dev/md0 may differ  depending on your configuration.

---

### Post by b0b138 on 2008-04-15
No, I don't think I installed ubuntu using raid. It didn't give me any prompts that I know of.

The last time I installed, I unplugged the drives that are being mirrored. After the install, I plugged them back in, and was able to mount my system drive, and my the mirrored drives separately.  This install, I left the mirrored drives plugged in, and I can mount the system drive and one of the drives to be mirrored. It shows the other drive but wont let me mount it.

Im assuming its software or fakeraid as the raid is built into the mobo. Promise fasttrack 378 or something like that.

I do not have mdadm installed.

---

