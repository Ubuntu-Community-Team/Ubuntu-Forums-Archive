---
title: "How to disable/uninstall software raid-1 using mdadm?"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by velvetGreen on 2007-03-26
Hello,

Here's my 'cat /proc/mdstat' at the moment: 

```
Personalities : [raid1]
md2 : active raid1 sdb4[1]
      1927680 blocks [2/1] [_U]

md1 : active raid1 sda3[0]
      259859328 blocks [2/1] [U_]

md0 : active raid1 sdb2[1]
      9767424 blocks [2/1] [_U]
```

My goal is to deactivate raid-1 completely and then remove md0, md1 and md2 so I can do a reinstallation using kubuntu alternative cd. 

By reading the bash man page on mdadm, I thought I can do uninstalling of raid-1 by first marking both active devices faulty, (i.e. sda2&sdb2) and then remove them from the array.

I tried:

```
sudo mdadm /dev/md0 --fail /dev/sdb2
mdadm: set /dev/sdb2 faulty in /dev/md0
tuomas@velvetGreen:~$ sudo mdadm /dev/md0 --remove /dev/sdb2
mdadm: hot remove failed for /dev/sdb2: Device or resource busy

```
 
So, as you can see, the other device is always busy and won't deactivate. 

Here's also the output of 'sudo mdadm --query --detail /dev/md0 /dev/md1 /dev/md2' if it helps:

```

/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Mar 26 02:37:01 2007
     Raid Level : raid1
     Array Size : 9767424 (9.31 GiB 10.00 GB)
    Device Size : 9767424 (9.31 GiB 10.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Mar 27 01:53:11 2007
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 22646411:3f10a9df:923160d0:bc6e7288
         Events : 0.20697

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
/dev/md1:
        Version : 00.90.03
  Creation Time : Mon Mar 26 02:37:13 2007
     Raid Level : raid1
     Array Size : 259859328 (247.82 GiB 266.10 GB)
    Device Size : 259859328 (247.82 GiB 266.10 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Mar 27 01:52:18 2007
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : c14b9d4c:ab12a019:3c4666a8:a28a9752
         Events : 0.12826

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       0        0        1      removed
/dev/md2:
        Version : 00.90.03
  Creation Time : Mon Mar 26 02:37:23 2007
     Raid Level : raid1
     Array Size : 1927680 (1882.82 MiB 1973.94 MB)
    Device Size : 1927680 (1882.82 MiB 1973.94 MB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Tue Mar 27 00:53:44 2007
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : fb144aae:22959a86:39cae05e:7ee37161
         Events : 0.36

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       20        1      active sync   /dev/sdb4

```

So how can I disable/uninstall my raid configuration?

**Edit:**

I also tried doing: 'sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan' but that gave:

```
 * Stopping RAID monitoring service mdadm --monitor                      [ ok ]
mdadm: fail to stop array /dev/md2: Device or resource busy
mdadm: fail to stop array /dev/md1: Device or resource busy
mdadm: fail to stop array /dev/md0: Device or resource busy

```

---

### Post by slackwarejosh on 2007-04-15
Alright,

I had the exact same problem today and finally figured out how to solve this.
I'll write up a n00b from the beginning in case I have to go back and find my solution later :) 



[SIZE="4"]**How to remove an MDADM Raid Array**[/SIZE]

1. Find out your arrays (md0, md1, etc..) using ```
 sudo fdisk -l 
```

2. Query your arrays to find out what disks are contained using ```
sudo mdadm --detail /dev/md0
 (or md1 or whatever)
```

3. Shut down the array using ```
sudo mdadm --stop /dev/md0
```

4. And here's the magic key ...... zero the superblock FOR EACH drive ```
sudo mdadm --zero-superblock /dev/sda (or hda)
sudo mdadm --zero-superblock /dev/sdX...
```

I hope I helped..I am pretty new to linux and software RAID, and I never join forums, but I just started using Ubuntu and it's so darn community-centric I just had to sign up and give back.

Keep Rockin! :guitar:

---

### Post by zaziork on 2007-04-29
3. Shut down the array using ```
sudo mdadm --stop /dev/md0
```

Before the above step, I needed to unmount the array first, otherwise I got the "device is busy" failure.

```
sudo umount /dev/md0
```

---

### Post by tomele on 2008-05-01
Great tip, thank you mate

---

### Post by lukaschemp on 2008-06-09
After remove software raid should I update grub with grub-install?

---

### Post by vinboy on 2008-06-25
thanks this is great info.

---

