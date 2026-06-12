---
title: "boot information"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-11-09
Where is the hard drive boot information? I know where it is in WindowsXP, but UBUNTU puts it before the xp boot information.  LInux Lime found a way to put it even before the Ubuntu boot info. I have an old install of Ubuntu 7.1 on hda3, then I Put  Ubuntu 7.1 on hda4(same drive). If I delete the hda4 partition I cannot boot into any partition including xp. I then install Ubuntu back on hda4. When I boot into the Ubuntu on hda4 I can see all my hda3 drive, When I boot to Ubuntu on hda3 I can't see or mount hda4. Strange probem. I need to know what files are in charge of the boot process so I might be able to edit it and put all my partition online. I have put much work into the Ubuntu on hda3 and would like to fix my booting problems rather than reinstall Ubuntu on hda3, which I think would solve my problem. If I reinstall I lose my history in email etc. If I could mount hda4 I might be able to back up hda3 to hda4 reinstall hda3 and backup hda4 to hda3. But I can't backup when the system does not recognize a partition(hda4). I can post any of the files you need. 


B. Ratliff

---

### Post by Harpoon on 2007-11-09
If my understanding is correct (it often is not), the problem source is having two insstallations of the same distribution, each on its own partition.  I can understand grub getting picky, since the boot files for each installation are stored on their own partitions.  I am guessing that one or the other needs to be "ignored" by grub in the boot process.

I was wondering if this type of setup was feasible, but I think you answered that question.  As to backing up data from either hda3 or hda4, I would suggest using a live cd (or other bootable disk) to accomplish that.  Since the CD is not relying on the grubs residing on the hard disk, it should allow you to see all of its partitions.

I apologize, in advance, for any inaccuracies.  As always, good luck.

---

### Post by Pumalite on 2007-11-09
Post>
sudo fdisk -lu
cat /etc/fstab

---

