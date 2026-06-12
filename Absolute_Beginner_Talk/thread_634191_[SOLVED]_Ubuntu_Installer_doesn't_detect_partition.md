---
title: "[SOLVED] Ubuntu Installer doesn't detect partitions"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mthakur2006 on 2007-12-07
Dear all,
I have a bit of a weird problem.
I have a 40 GB hard disk which has Ubuntu on it. I have done numerous installs of Ubuntu (and other distros on it, no problem at all).
Then I decided to try out PC BSD and it installed allright. I resized the Ubuntu partition and created a 7 GB partition for it. I didn't like PC BSD so I decided to try out Mandriva. It's installer said that I could not create or delete partitions, but it detected my partitions and I just changed the mountpoint of the BSD one to / in mandriva and it installed fine and runs fine. Its even got a nice GRUB.
I tried Suse as well but it gave the same errors and didn't install at all.
Then I have grown to dislike Mandriva and want to put Ubuntu on my other partition as well, so when I put the alternate CD in and it didn't detect any partitions, it just says 40.0 GB Hard disk. I tried Gparted as well, but the same thing occurs: it just shows the space as unallocated.
If I do ```
 sudo fdisk -l 
``` from my current Ubuntu or Mandriva installation, it gives me the results of partitions.
Can you help, please?
Thanks.

---

### Post by mthakur2006 on 2007-12-07
bump

---

### Post by mthakur2006 on 2007-12-08
bumpp

---

### Post by louieb on 2007-12-08
I belive Mandrivea uses Diskdrake.  Diskdrake can do non-standard things to your partition table  bet you have a primary partition inside the extended partition. That will cause any of the parted family of partitioner's to stop and not do anything. 
Post your fdisk -l but the short of it is if Diskdrake  caused the problem then your going to have to use Diskdrake to fix it,

---

### Post by mthakur2006 on 2007-12-08
Here's my sudo fdisk -l ```
 mtha@ubuntu:~$ sudo fdisk -l
[sudo] password for mtha:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            4804        4864      489982+  82  Linux swap / Solaris
/dev/sda2   *           1        3824    30716248+  83  Linux
/dev/sda3            3886        4864     7863817+  a5  FreeBSD
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order
mtha@ubuntu:~$ 

```

Thanks for the reply. How would I go about undoing it?
Thanks.

---

### Post by MrHippocampus on 2007-12-08
You could try using the "testdisk" program to try and recover the partition table. Ive never used it myself but a lot of people swear by it. Google should yield some useful info on it.

---

### Post by mthakur2006 on 2007-12-08
> **MrHippocampus said:**
> You could try using the "testdisk" program to try and recover the partition table. Ive never used it myself but a lot of people swear by it. Google should yield some useful info on it.

cool thanks.
i will have a go and get back to you :)

---

### Post by gn2 on 2007-12-08
If there's nothing on the drive you want to keep you could just wipe the thing completely clean with DBAN: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then start from scratch effectively with a brand new hard drive.

---

### Post by mthakur2006 on 2007-12-08
nah thanks for the suggestion but i have got quite some data on it :)
i think i have fixed it, i booted into mandriva and played about with partitions so that they are not overlapping anymore but now the partition entries are not in order anymore.
any ideas?

thanks.

p.s. here's my new sudo fdisk -l
```
 mtha@ubuntu:~$ sudo fdisk -l
[sudo] password for mtha:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000eb31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        3824    30716248+  83  Linux
/dev/sda3            3886        4864     7863817+  a5  FreeBSD
/dev/sda4            3825        3885      489982+  82  Linux swap / Solaris

Partition table entries are not in disk order
mtha@ubuntu:~$ 

```

---

### Post by louieb on 2007-12-08
Partition table looks fine.  Just 3 primary partitions. The fact they are not  in disk order should not cause any problems. Don't see any reason  for the Ubuntu installer not to pick up the partitions now.
BTW: The System Rescue CD has GParted  and testdisk on it. NIce CD to have laying around - never know when you might need it - link in signature.

---

### Post by mthakur2006 on 2007-12-08
guess what, the installer picks up the partitions all right now.
Thank you all who have helped =D

---

