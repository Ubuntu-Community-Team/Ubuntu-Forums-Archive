---
title: "Help with resizing new install partition"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-24
I currently am triple booting between ubuntu, xp and vista. I have the partitions set up as follows on my 320 GB Seagate:

Local Disk (C:)  NTFS  20GB Primary    //XP Pro install
(*) Extended 200GB  Primary             //automatically created - not sure about this
Data (F:) 198 GB NTFS Logical           //partition to store recorded tv, movies, music , etc.
SWAPSPACE2 (*) Linux Swap 2.8 GB  Logical  //Ubuntu automatically created - assuming by the name it is the swap space
Local Disk (*) Linux Ext3 65 GB Primary //Ubuntu install - I want to resize this partition to around 20 - 30 GB
Vista (v:) NTFS 20 GB Primary             //Vista install

I want to resize the 60+ Ubuntu partition to around 20 - 30 GB, and then move the freeded space (unallocated space) this will create into my Data (F) partition. Does anyone know how this can be accomplished?

---

### Post by LaRoza on 2007-05-24
When altering partitions, a risk of data loss exists, so backup first.

You can shrink the Ubuntu partition, and expand the other partition into that area.

I would suggest you use a live cd, GParted, to do this.

-edit With so many OS's on one disk, getting a second hard disk would be a good idea.

---

### Post by ukripper on 2007-05-26
> **jba6511 said:**
> I currently am triple booting between ubuntu, xp and vista. I have the partitions set up as follows on my 320 GB Seagate:

Local Disk (C:)  NTFS  20GB Primary    //XP Pro install
(*) Extended 200GB  Primary             //automatically created - not sure about this
Data (F:) 198 GB NTFS Logical           //partition to store recorded tv, movies, music , etc.
SWAPSPACE2 (*) Linux Swap 2.8 GB  Logical  //Ubuntu automatically created - assuming by the name it is the swap space
Local Disk (*) Linux Ext3 65 GB Primary //Ubuntu install - I want to resize this partition to around 20 - 30 GB
Vista (v:) NTFS 20 GB Primary             //Vista install

I want to resize the 60+ Ubuntu partition to around 20 - 30 GB, and then move the freeded space (unallocated space) this will create into my Data (F) partition. Does anyone know how this can be accomplished?


Easiest , safest and simplest way to resize your current ext3 is by using Partition Magic 8 which redistributes your free space how you want it. I have tried Gparted but with it you can only resize partitons next to the current one what if you want to resize  a partition which is in the middle and no where to resize left/ right then PM8 is very Handy tool. I would say one of the best., PM8 can even select your unallocated space and redistribute among the required partitions even extending the file system and also the SWAP space.

---

