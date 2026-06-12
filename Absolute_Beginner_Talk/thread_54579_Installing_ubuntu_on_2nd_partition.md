---
title: "Installing ubuntu on 2nd partition"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by SalCro.Di on 2005-08-05
Hi,

I would like to install ubuntu on my 2nd partition on my computer without erasing files that are on the 2nd partition. Can i do this ? or not?

All my partitions are ntfs so i think they need to be fat32, so prolly i'll need to format my 2nd partition ????


grtz

---

### Post by crmanski on 2005-08-05
You would have to backup those files(to DVD, CDR, etc...), then  install ubuntu on that partition, and later on copy them back.  As far as I recall you need to format the partition when doing the default installation onto a partition.
The wiki mentions this a little bit...
[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by xmastree on 2005-08-05
As I understand it, the way to go is to reduce the size of the second partition (after backing up, of course). This creates free space, which ubuntu will use.

If you wish to write to that partition with linux, it'll need to be FAT32. NTFS can be read, but not written.

---

### Post by mejohnsn on 2006-07-18
I'm too new here to speak with absolute confidence myself, but I think you are wrong here. He need to do FAT32 only if he wants to read/write that partition from _both_ Ubuntu and Windows. If he wants to read/write the new partition from Ubuntu only, he can (and should) use ext3.

But don't take my word for it; see the excellent source on partitioning issues written by another Ubuntu member, [http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html). I would read the whole thing before making any decisions about what the final partitioning should look like.

---

### Post by starscalling on 2006-07-18
i believe when you do the manual partitioning in the install
you should be able to choose to install / on that partition
just check that its set to _not_ delete data
though ive had trouble making /home directories on fat32 partitions...
but that was  a seperate partition than my / :) anyway take a look at that bit in the install :P

---

### Post by xmastree on 2006-07-19
> **mejohnsn said:**
> He need to do FAT32 only if he wants to read/write that partition from _both_ Ubuntu and Windows.That's perfectly true. I was assuming that since he wanted to put linux on the second partition, there was a windows installation on the first with which he wants to share files.
> I would read the whole thing before making any decisions about what the final partitioning should look like.Well, since it was last August, I would hope that the decision has been made by now... :rolleyes:

---

