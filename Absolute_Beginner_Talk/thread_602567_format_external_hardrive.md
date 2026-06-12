---
title: "format external hardrive"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Fangus on 2007-11-04
quick n00b question how do i format an nfts drive in ubuntu to whatever ubuntu uses, as that drive is suddenly been changed to read only, or can i just stop it being read-only (ive tried using the properties box.) thanks

---

### Post by llamakc on 2007-11-04
> **Fangus said:**
> quick n00b question how do i format an nfts drive in ubuntu to whatever ubuntu uses, as that drive is suddenly been changed to read only, or can i just stop it being read-only (ive tried using the properties box.) thanks


The GUI way would be to use GParted. IF the drive has data on it and you still want access to it install [ntfs-3g]("apt:ntfs-3g") in Synaptic (or click on the apt-url link). That will allow to have read-write on the NTFS partition.

---

### Post by chamberlain2006 on 2007-11-04
I would reccomend using the program "Synaptic" (System>Administration>Synaptic Package Manager) and installing "gparted".  Then, go to System>Administration>Partition Editor, and format the partition to ext3

---

### Post by Fangus on 2007-11-04
unfortunately its not as simple as that as i have no internet with ubuntu, thanks

---

### Post by chamberlain2006 on 2007-11-04
You can do it manually... do "sudo fdisk -l" in terminal to find the partition name... probably something like "/dev/sda1" and then do "sudo mkfs.ext3 /dev/whatever" to format it.

---

### Post by cmnorton on 2007-11-04
What about fdisk and mkfs from the command line?

---

### Post by Fangus on 2007-11-04
great that formated my primary drive, it doesnt matter too much though as im moving to xp

---

### Post by llamakc on 2007-11-04
> **chamberlain2006 said:**
> You can do it manually... do "sudo fdisk -l" in terminal to find the partition name... probably something like "/dev/sda1" and then do "sudo mkfs.ext3 /dev/whatever" to format it.

Yes this can be done in the terminal. No you won't do it by 'fdisk -l'. You would need to a) unmount the partition, b) use fdisk to manually delete the partitions and create Linux partitions on it, and then c) use the appropriate mkfs.*** command to create the filesystem ON the partition. This is all done on an UNmounted drive.

"fdisk -l" returns information about the drive and does not alter anything.

```

ken@llamakc 09:39:31:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a9a1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         127     1020096   82  Linux swap / Solaris
/dev/sda2             128        6502    51207187+  83  Linux
/dev/sda3            6503       19457   104061037+  83  Linux

```

If you choose to do this through the terminal, run "sudo fdisk -l" without any particular drive designation after it. The results will be all of the disks currently in use.

BTW, isn't GParted installed by default? Same with ntfs-3g in Gutsy? You probably have the tools already on your system. Just decide if you want to keep the drive as ntfs or not.

---

### Post by llamakc on 2007-11-04
> **Fangus said:**
> great that formated my primary drive, it doesnt matter too much though as im moving to xp

Sorry you got bad advice. Good luck no matter what your decision is. If the forums hadn't been on 'maintenance' my post may have saved you.

---

### Post by Fangus on 2007-11-04
yep, ah well, i didnt have much stuff lost, i chose xp simply for cmpatibilaty issues thanks guys!

---

