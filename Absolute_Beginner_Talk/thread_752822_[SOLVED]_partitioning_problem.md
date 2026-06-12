---
title: "[SOLVED] partitioning problem"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by dmongo on 2008-04-12
After doing a manual partitioning on Xubunto partiion manager  and clicking install  i get a  

The ext.3 file system creation in partition #2 of SCSI1 (sda) failed. 
 
how do i fix this..

---

### Post by tamoneya on 2008-04-12
make sure that you do not have the partition mounted while you try to change it.  This typically means that you should do all partition editing from the liveCD.

---

### Post by dmongo on 2008-04-12
i was doing it off of the live cd   how do you unmount it

---

### Post by NightwishFan on 2008-04-12
You did the partitioning in the install or with gparted?

If you did from within the install and it failed please check your cd for errors, as the same thing happened to me today.

---

### Post by dmongo on 2008-04-12
i first partitioned with gparted then when i went to install i ended up doing it all over again with the partition manager.   i check the cd for errors and  hashmarks   no errors and the hashmarks matched... how do you unmount the partion once you start to install.

---

### Post by NightwishFan on 2008-04-12
I do not think you can. Try to delete all the partitions into free space and use the partitioner in the install application.

---

### Post by dmongo on 2008-04-12
thats what i did last time   do you still have to unmount the partintions or they already are because there free space.

---

### Post by dmongo on 2008-04-12
thanks for everyones help   i think i figured it out..

---

