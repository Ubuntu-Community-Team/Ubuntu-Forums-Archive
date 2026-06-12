---
title: "Creating Swap File. Preceding and Following Fre Space Sizes?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by universalis13 on 2008-02-20
What's with this Free Space Proceeding (MiB) and Free Space Following (MiB)? I'm creating a swap file and then a ext3. Ultimately I want to create dual boot XP/Linux system.

First off, do I "Create as:" Primary Partition or Extended Partition. I have "linux-swap" selected for my Filesystem.

Secondly, what do I set my "Free Space Preceding" and my "Free Space Following" to?

Thanks

---

### Post by tyggna1 on 2008-02-20
Unless you have more than four (4) partitions, make all of them primary.  Free space proceeding and following just lets you round to the nearest hard drive block (cylinder is the correct term).  You should never need more than 8Mb in those on modern hard drives, and ideally you don't really want any.

Best way to get what you want is to install Windows first, and leave a bunch of empty space on your hard drive.  Once windows is up, install Linux on the remaining portion of the drive.

Alternatively, if Windows is already installed, use gparted to resize your windows partition after running an
```
chkdsk /r
```
in the windows command line (this will require you to reboot into windows after you've given the command).  Once it's resized, you can make two more primary partitions for Linux--an ext3 and a swap (though some people prefer to make three, one for your home directory--that way, if you have to reinstall Linux, you don't lose any pictures, movies, or other personal data).

---

### Post by universalis13 on 2008-02-20
Thanks,

I'll give it a try.

---

