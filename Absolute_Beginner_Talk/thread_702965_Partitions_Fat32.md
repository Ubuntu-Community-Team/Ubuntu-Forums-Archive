---
title: "Partitions: Fat32?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by twodayslate on 2008-02-20
Here is what I want for my partiotions
> 1GB swap primary beginning
1GB /boot ext3  primary beginning
8Gb of / ext3 primary beginning
rest_of_space /home fat32  primary beginning

I want a fat32 so Windows will recognize the drive. But the partitioner says it will not do Fat32. What is windows safe and good?

Thanks for the help!

edit:// Right now I have Linux on one drive and windows on another.

---

### Post by Origin415 on 2008-02-20
In the LiveCD, instead of using the installer's partitioner, open System -> Administration -> Partition Editor, that program should handle Fat32

Also, 1GB is ginormous for a /boot. If your going to make one at all, ideally it would be around like 30MB or so -- that will give you plenty of room. All thats in /boot is a kernel or two and grub's configuration.

---

### Post by twodayslate on 2008-02-20
Kernals are that small?

So /home can be fat32 and / can be ext3.
Is ext2 better than 3?

---

### Post by ve9gj on 2008-02-20
> **twodayslate said:**
> Kernals are that small?

So /home can be fat32 and / can be ext3.
Is ext2 better than 3?

ext3 is considered better than ext2. Ext3 has a journal helps clean up quicker after a power failure etc.
I would let home be ext3 and if you want to access it it from windows check out:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
It allows you to have linux ext2 or 3 partitions available as a drive letter in Windows.  Works great!

---

### Post by PeterJS on 2008-02-20
Ext3, is Ext2 + Journaling, so it's better in so far as it's newer and handles crashes much more elegantly because it can use the journal to reconstruct and salvage any partial disk operations.

How ever using a fat32 /home/ is not going to work because fat32 does not support real permissions and many programs, especially those dealing with any sort of sensitive data (passwords, etc), will not run. I know that wine won't run because the ownership will be wrong.

Also you can read ext3/2 from windows with:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Origin415 on 2008-02-20
I'm not sure how large Ubuntu kernels are offhand, but my Gentoo boxes kernels are about 2MB. Ubuntu's are probably 8MB max, including the initrd, etc.

ext3 is only different from ext2 by the use of a journal, with helps with dealing with and preventing filesystem errors, so ext3 is better.

---

### Post by twodayslate on 2008-02-20
So ext3 for all should be good and compatible with windows.

Should I add anymore partitions?

---

### Post by ve9gj on 2008-02-20
> **twodayslate said:**
> So ext3 for all should be good and compatible with windows.

You will have to install the software/driver from [http://www.fs-driver.org](http://www.fs-driver.org) in Windows to see the Linux ext3 filesystems.

> **twodayslate said:**
> Should I add anymore partitions?
I wouldn't.  No need to now.

---

