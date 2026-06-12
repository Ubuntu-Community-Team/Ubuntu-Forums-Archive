---
title: "RAID (mdadm) - /dev/sdx or /dev/sdx1"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Rob_Quads on 2007-03-24
I have just created a RAID5 array on my file server but I have noticed that there are some differences in the docs that are around. I used the following command

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sde /dev/sdf /dev/sdg

and when I look at the table of the disks using fdisk it shows nothing on the discs. I noticed that some docs about creating a RAID mention you should format the disks and give them the RAID autodtect type and then create the array using

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sde1 /dev/sdf1 /dev/sdg1


So Whats the difference between the two. Have I built an array that cannot be moved between machined? I have ready that it needs to be on autodetect to be able to be moved to another machine?

---

