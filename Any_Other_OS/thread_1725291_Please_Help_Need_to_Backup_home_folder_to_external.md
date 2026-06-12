---
title: "Please Help: Need to Backup home folder to external drive via terminal"
date: 2011-04-09
forum: Any Other OS
---

### Post by noob555 on 2011-04-09
Hello all.  I have apparently broken my installation, though I am uncertain how.  I can boot into the terminal, but the desktop shell refuses to load under any circumstances.  The best thing I can think of is to simply reinstall.  

But before I reinstall, I need to backup my home folder to the external drive.  

I found a program called rsync that seems easy enough, but I cannot figure out the location of my external usb drive.


Can anyone tell me how to do this?

Please?


FYI, I'm using Linux Mint 9

---

### Post by Perfect Storm on 2011-04-09
Moved to Other OS/Distro Talk.

---

### Post by mips on 2011-04-09
Double post.

---

### Post by mips on 2011-04-09
> **noob555 said:**
> 
I found a program called rsync that seems easy enough, but I cannot figure out the location of my external usb drive.

Can anyone tell me how to do this?

Please?


You are on the right tract.


```
sudo fdisk -l
```

I just inserted 4GB flash drive to test it and it is picked up as:
> Disk /dev/sdi: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008c349

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1         490     3932128+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(488, 254, 63) logical=(489, 135, 30)

In my case it is /dev/sdi1 but for you it will be different.

---

