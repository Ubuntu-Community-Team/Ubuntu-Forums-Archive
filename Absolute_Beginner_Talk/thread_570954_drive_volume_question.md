---
title: "drive volume question"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-08
I have two hard drive in my ubuntu box. Ubuntu says that my 80 Gig drive is 49.9 gigs.
I understand that I will loose some of the capacity due to simple math and slack space.
at least that was the way it was in windows.  Anyway I only expected to loose a few gigs not 30.

When I installed ubuntu on this box. it was installed on the first drive. so I believe the three partitions linux makes on a drive were made on that one. my home directory is mounted on the second drive.  This is the way I wanted it but I don't understand why I am missing 30 gigs.

can someone please shed some light on this for me.

thanks

---

### Post by Shazaam on 2007-10-08
Please Copy and paste output from terminal...
```
sudo fdisk -l
```


(small L)

---

### Post by Pumalite on 2007-10-08
Post also:

df -h

---

### Post by rdsii64 on 2007-10-08
rdsii64@rdsii64-Ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4842    38893333+  83  Linux
/dev/sda2            4843        4982     1124550    5  Extended
/dev/sda5            4843        4982     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       49736    25066912+   7  HPFS/NTFS
/dev/sdb2           49737       51267      771624   82  Linux swap / Solaris
/dev/sdb3           51268      155061    52312176   83  Linux
rdsii64@rdsii64-Ubuntu:~$ 


Above the result of the fdisk command

---

### Post by rdsii64 on 2007-10-08
> **Pumalite said:**
> Post also:

df -h

rdsii64@rdsii64-Ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  7.5G   28G  22% /
varrun                189M  104K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
procbususb            189M  104K  189M   1% /proc/bus/usb
udev                  189M  104K  189M   1% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   33M  156M  18% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1              24G   66M   24G   1% /media/disk
/dev/sdb3              50G  6.1G   44G  13% /media/disk-1
rdsii64@rdsii64-Ubuntu:~$ 


above is the relust of df-h

---

### Post by Pumalite on 2007-10-08
You posted from sda1 and is correct. Your sudo fdisk -l sees your sdb well too.

---

### Post by rdsii64 on 2007-10-08
> **Pumalite said:**
> You posted from sda1 and is correct. Your sudo fdisk -l sees your sdb well too.

Once you gave me the command I could see what I needed to see for myself. thank you for your help. I have written that command on my Linux scribble pad so when I need that info again I will have one more tool in my box.

thanks

---

### Post by Pumalite on 2007-10-08
You are welcome. Happy Ubuntuing!

---

