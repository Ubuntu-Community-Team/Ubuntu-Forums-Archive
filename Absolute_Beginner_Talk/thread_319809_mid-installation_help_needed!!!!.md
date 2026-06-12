---
title: "mid-installation help needed!!!!"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by dross on 2006-12-16
Hello,
I was half-way through installation and the installer threw the error: invalid file system type for mount point...here's my partition scheme:

40 MB fat16 Dell partition (primary)  -- sda1
50 GB ntfs Dell Windows partition (primary) -- sda2
20 GB extended partition -- sda4 {
   8 GB ext 3 logical partition to be used as / -- sda5
   2 GB linux-swap logical partition to be used as /swap -- sda6
   11 GB fat32 logical partition to be used as /home --sda7
}
3 GB fat32 Dell restore partition (primary) ---sda3

Any help would be appreciated, as the new partitions have already begun to be created (they had some data written to them before install failed!)

Thanks!

---

### Post by mcduck on 2006-12-16
/home should be Ext3 too, Fat can't understand linux user and file permissions.

---

### Post by dross on 2006-12-16
ok...but I won;t be able to share that /home with Windows? is there any file system type i can use in my partition that will allow me to share??

---

### Post by dross on 2006-12-16
By the way, I should also say thanks for the quick response...errors in the middle of installation are not fun!

---

### Post by mcduck on 2006-12-16
There are some very nicely working Ext2/3 drivers for Windows, that's how I'm doing it. (not that I'd even remember when I used windows last time ;))

edit: [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by Bachstelze on 2006-12-16
> **dross said:**
> ok...but I won;t be able to share that /home with Windows? is there any file system type i can use in my partition that will allow me to share??


I recommend you leave the /home partition alone and use anonther one to share data with Windows.

---

### Post by dross on 2006-12-16
alright, changed /home from fat32 to ext3...as I'm waiting for the install...another quick question...how am I going to distinguish between which partition I want to boot from...I assume I'll have to switch it in the bios, but I don;t remember ever seeing a partitioning scheme in there, just a choice to boot from disk, or cd, etc...

---

### Post by Sef on 2006-12-16
> how am I going to distinguish between which partition I want to boot from

With a dual boot, Ubuntu is the default operating system, but you will have the option to boot into windows.  Just push the down arrow within the time limit (30 seconds, i think.)

---

### Post by mcduck on 2006-12-16
yes, Ubuntu will install you a nice boot menu where you can choose which OS you want to use. The default timeout is 10s (and that can be changed later, as well as default OS)

---

### Post by Sef on 2006-12-16
> The default timeout is 10s

Thanks for the correction.

---

### Post by dross on 2006-12-16
Thanks everyone for all the help.  The installation went fine and now I'm writing from my installed Ubuntu OS.  Thanks!

I have been using Ubuntu for about a year, but on an old Dell desktop, so it ran prohibitatively slow for a lot of tasks that I needed to do.  I'm very happy now to be able to use it in my daily work!

A quick question, I have the three Dell partitions mounted on my Desktop...is there any way to remove those; I don;t see why I would need to be writing anytthing to those (if I have write ability)...

---

