---
title: "Raid 5 question"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by SmokeMasta on 2007-12-04
I had a drive fail earlier and i replaced the drive.
but when i do cat /proc/mdstat it doesnt show as rebuilding.
i just see the 3 drives in my raid 5 array and the 4th drive isnt on there.

how do i reassemble the array using that new drive to replace the broken one ?

---

### Post by stijn_pol on 2007-12-05
If your existing array is named md0 and you want to hot add /dev/sdb1, type:
```
sudo mdadm --add /dev/md0 /dev/sdb1
```

(Supposing you have create partitions, filesystem on the new disk)

See [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server) for more information

---

