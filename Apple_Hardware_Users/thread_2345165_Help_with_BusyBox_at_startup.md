---
title: "Help with BusyBox at startup"
date: 2016-12-01
forum: Apple Hardware Users
---

### Post by cashedj01 on 2016-12-01
[COLOR=#111111][FONT=Ubuntu]I just started using Ubuntu for a school project. So I am running it off an external hard drive on my Macbook. Initially I couldn't start-up because of a GRUB error so I installed Disk-repair. Now, I can't even use the OS. This is what it shows every time I try to:[/FONT][/COLOR]
   ```
[   3.213053] sd 1:0:0:0:  [sdc] No Caching mode page found
   [   3.213054] sd 1:0:0:0:  [sdc] Assuming drive cache: write through
   /dev/sdc2 contains a file system with errors, check forced,
   Inodes that were part of a corrupted orphan linked list found

   /dev/sdc2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e.. without -a or -p options)
   fsck exited with status code 4
   The root filesystem on /dev/sdc2 requires a manual fsck


   BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
   Enter 'help' for a list of built-in commands

   (initramfs)
```
[COLOR=#111111][FONT=Ubuntu]I googled this and found a solution online where I had to run in a bootable ISO flash drive[/FONT][/COLOR]
    ```
fsck /dev/sdc2/ 
```
[COLOR=#111111][FONT=Ubuntu]but the thing is sdc2 does not exist, when I unplugged and plugged my external hard drive and held tab down after "fsck /dev/sd what I saw were[/FONT][/COLOR]
    ```
sde sde1 sde2
```
[COLOR=#111111][FONT=Ubuntu]Please help me, I don't know what to do.[/FONT][/COLOR]

---

### Post by howefield on 2016-12-01
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by cashedj01 on 2016-12-01
I was able to fix this problem. Now my Ubuntu 16.04 LTS doesn't show the Wireless Networks available, I check the driver and it's using the Broadband...

Can anyone help?

---

