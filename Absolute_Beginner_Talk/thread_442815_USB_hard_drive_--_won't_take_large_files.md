---
title: "USB hard drive -- won't take large files"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by infrarad on 2007-05-13
Hi,

I have a new USB hard drive (300ish gb). I can get it to automount, and it's been formatted. I am able to copy a file of document size to it, but when copying something large like a movie, it will copy part of it, and then the time-to-complete timer will increment to ridiculous time periods, and I can't cancel the copy process. (Just with the cancel button--I figure there is a kill command from the terminal that I don't know).

I have no ideas--this is really my first time attempting to understand the guts of a system, of any operating system.

Thanks!

---

### Post by Happy_Man on 2007-05-13
Is it formatted as FAT32? That kind of format can't take files larger then 4 GB, which movies undoubtedly are.

---

### Post by dpzektor on 2007-05-13
I recently purchased an Iomega 320GB USB drive (nice drive too!) and had the same problem. It was of course because they default format it to Fat32 which has a 4GB file limitation. I re-formatted the drive to Ext3, and it works great. If you do plan on using it on a Windows machine as well however, you may want to format it NTFS (from within Windows) and then install the NTFS read/write in Ubuntu. That can easily be installed using Automatix. Hope that helps!

---

### Post by infrarad on 2007-05-13
I couldn't tell you--I was also having difficulty formatting it from this machine, so a friend formatted it with a laptop (also running Linux, I think Debian). The return from fdisk -l is

```
Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38913   312568641   83  Linux

```

Also, a new bit of information: I copied a directory of comics files (around 8-15mb each) and some of the files successfully made it (i.e., I'm able to open them), but after about ten, the copy process hung.

---

### Post by sparrowkc on 2007-12-14
I am having the same problem with a drive that is ext3.  Did you ever get it to work?

Edit: I solved my problem by bypassing an overloaded usb hub.

---

