---
title: "Wrong free space"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by nefhyg on 2008-02-10
Hello.

For some strange reason I have much less free space I supposed to have (ext3 partition)

df results   Size   Used Avail Use%   
/dev/sda5  101G  91G  200M 100%

Where is the 10GiB free I supposedly have?

So I run the e2fsck and nothing. Then I run the check from gparted on the live cd, and after the e2fsck it decides by itself to grow the partition, but then it says: " filesystem is already blah blocks long" and does nothing.

Help please.

---

### Post by nefhyg on 2008-02-10
No one knows? I could post more info if needed...

---

### Post by Herman on 2008-02-10
Yes, please post more info.

The most common cause for the symptoms you seem to be describing is that the file system is not enlarged to fill the partition.
This can happen after restoring from a partimage backup or using a 'dd' command to restore the whole operating system from a backup made with a 'dd' command.
The partition made for restoring to must always be at least as large or little larger than the original partition was under those circumstances. However, if the file system is not enlarged to fill the partition, hard disk space may be wasted and false indications about the amount of free space are the usual result.

If you have an ext2 or ext3 file system, then resize2fs is the command to use for adjusting the size of the file system to fit the partition properly.
```
sudo resize2fs  /dev/sda5
```Where" /dev/sda5 is the partition number, please replace with whatever is appropriate for your particular computer, according to output from 'sudo fdisk -lu' command or looking with GParted or similar.

The file system check you already ran from GParted should have already run resize2fs for you though, so I don't understand why that didn't fix it already.

Maybe you simply need to try again or maybe something else is wrong.
Please post at least the output from sudo fdisk -lu, as well as any more information you think might be relevant.
```
sudo fdisk -lu
```Regards, Herman :)

---

### Post by nefhyg on 2008-02-10
Thanks a lot for replying, I just found out the problem.

I had a reiser partition, and changed it to a ext3. I didn't know that ext3 reserves a % of each partition for the root...

So, you just have to tune a newly created partition using tune2fs. It makes no sense to have another partition (besides the /) with a reserved space.

Thanks for replying, I hope it helps someone else.

---

