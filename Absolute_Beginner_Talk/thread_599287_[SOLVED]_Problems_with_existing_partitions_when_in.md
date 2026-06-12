---
title: "[SOLVED] Problems with existing partitions when installing Ubuntu."
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by gs110 on 2007-11-01
When I try to partition My drive for Ubuntu(7.10) in the installation, it gives me this message:

File system doesn't have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of clusters is 28034 (55960 expected); size of FATs is 110 sectors (219 expected).

Then when I go back to try and fix it, I get this message:

The test of the file system with type fat16 in partition #1 of SCSI1 (0,0,0) (sda) found uncorrected errors.
If you do not go back to the partitioning menu and correct these errors, the partition will be used as is.

The partition table that I tried to create looked like this:

Device Type Mount point Format? Size Used
/dev/sda
/dev/sda1 fat16 /media/sda1 57MB 33MB
/dev/sda2 ntfs /media/sda2 83922MB unknown
/dev/sda5 ext3 / 159998MB unknown
/dev/sda6 swap 1028MB unknown
/dev/sda3 fat32 /media/sda3 4984MB 4200MB
unusable 8MB

Thanks for any help.

---

### Post by erginemr on 2007-11-01
It seems there is a small (57 MB) partition formatted in FAT 16 in your hard disk, reported as sda1. Assuming that your main Windows partion is sda2, formatted in ntfs with 83 GB, what is this 57 MB space used for? Are you actually using this part or can it be a residue from an earlier windoes installation? 

I could suggest you to get rid of this part by combining it with another partition, say sda3 with fat32 (this is easier said than done), but by backing up the information on them first into your main ntfs drive.

---

### Post by erginemr on 2007-11-01
On a second thought, I think you may go on with the installation. GParted will not touch that part anyway during the repartitioning process...

---

### Post by gs110 on 2007-11-01
Yeah nothing bad seemed to happen when I installed it, thanks.

---

### Post by erginemr on 2007-11-01
> **gs110 said:**
> Yeah nothing bad seemed to happen when I installed it, thanks.

You are welcome. Happy 'bunting.

---

### Post by peterwr on 2007-11-26
Is this a Dell machine, by any chance? I'm just upgrading a Dell and it has exactly that partition (and error message). 

Just FYI. 

HTH (and here goes...)

---

### Post by drizad on 2007-11-28
Hi guys,

I have the same problem here, with my ACER notebook. I think my new small partition of fat16 (just 8MB) was created during my last installation with Xandros, which I dual boot with WinXP.

Initially, I was quite surprised to see that Ubuntu installer said that it was a "bug" and I did not proceed with the installation, until I saw this thread.

I did try to reformat the partition to fat32 with Ubuntu FF 7.04, but failed, and I just continue to install it.

Now my notebook is dual booting Ubuntu FF (will upgrade to GG soon) with WinXP, wiping my Xandros OCE 3.0.2...

Cheers!

---

