---
title: "GParted won't let me add a partition to an empty hard drive. what the heck?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-06-12
i'm running ubuntu 7 on a dedicated machine, the OS is installed on one hard drive, and i'm trying to install a second drive for more space. 

when i fdisk the drive, i get the error message :
Warning : invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

and no matter how many times i set up a new partition and write it to the disk, it will say that same error message next time i fdisk it.

in gparted more problems. it shows the drive (although listed as a 280gig instead of 300) as one giant "unallocated" partition. i click the tool to make a new partition and it says i need to set a disklabel before i can partition. no matter how many times i set it, i get the same error message when i try to add a parition.

what's the deal?

---

### Post by Najand on 2007-06-12
Do:
```

sudo fdisk DRIVENAME

```
Change DRIVENAME with your drive name, i.e. /dev/hda or /dev/sda, etc.
and then when you recieved the error:
"Warning : invalid flag 0x0000 of partition table 4 will be corrected by w(rite)"
push "w" key and wait until it fix your problem.
Then try again partitioning.

---

### Post by ijason on 2007-06-12
how many times should i try before i assume that it's being untrue when it tells me that simply w(riting) the partition table will fix it?

i've tried your suggestion 5 times now and still get the error message. :(

---

### Post by Najand on 2007-06-12
Hmm, try "sudo fsck DRIVENAME" command and if it didn't help,
better to download Gparted live CD and try partitioning using that.
 It works much better than the gparted shipped by ubuntu.

---

### Post by ijason on 2007-06-13
ok, i'm downloading it now. i'll let you know if that solves the problem. 

thanks for the suggestion :)

---

### Post by ijason on 2007-06-13
**naj**
when i boot off the gparted live-cd, it doesn't show my second hard drive on the pull-down list of devices. only the first - and properly working - hard drive.

---

