---
title: "fsck + chdsk = windows recovery? Please Help!"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Sand Lee on 2008-01-17
Ok, so I booted up Ubuntu and it ran fsck, but this time it took an unusually long amount of time to finish. I then rebooted into windows and it ran it's chkdsk and gave me the following output:

```
Checking file system on C:

The type of the file system is FAT32.





One of your disks needs to be checked for consistency. You

may cancel the disk check, but it is strongly recommended

that you continue.

Windows will now check the disk.                         

Volume Serial Number is 320D-180E

\WINDOWS\repair\software  first allocation unit is not valid. The entry will be truncated.

\WINDOWS\repair\security  first allocation unit is not valid. The entry will be truncated.

\WINDOWS\repair\sam  first allocation unit is not valid. The entry will be truncated.

\WINDOWS\repair\DS_SAM  first allocation unit is not valid. The entry will be truncated.

\WINDOWS\repair\DS_SECURITY  first allocation unit is not valid. The entry will be truncated.

\WINDOWS\repair\DS_SOFTWARE  first allocation unit is not valid. The entry will be truncated.

The \WINDOWS\system32\config\system.LOG entry contains a nonvalid link.

The size of the \WINDOWS\system32\config\system.LOG entry is not valid.

Bad links in lost chain at cluster 196610 corrected.

Convert lost chains to files (Y/N)? Yes

262112 KB in 1 recovered files.

Windows has made corrections to the file system.

     27497856 KB total disk space.

        17504 KB in 306 hidden files.

        15840 KB in 974 folders.

      2927712 KB in 18199 files.

     24536784 KB are available.



        16384 bytes in each allocation unit.

      1718616 total allocation units on disk.

      1533549 allocation units available on disk.

```
After this happened Windows when into the loading screen but instead of the green bar at the bottom, it said "Please wait..." . After that, the windows installation screen started!!!:mad: I promptly shut off the PC and booted into Ubuntu in an attempt to recover my data, but it seems it has all been formated... Please help. The only hope in restoring my data, it seems, is a file found0000.chk.

---

### Post by Dynaflow on 2008-01-18
What do you get from the terminal when you enter ```
cat /etc/fstab
```?

---

