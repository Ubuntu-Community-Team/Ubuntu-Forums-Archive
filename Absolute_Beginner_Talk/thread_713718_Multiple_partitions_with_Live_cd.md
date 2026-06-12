---
title: "Multiple partitions with Live cd?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by regbsn on 2008-03-03
Can I make a "/" , a "/ home" and a swap partition with a "live CD"?

I downloaded and burned a live Ubuntu 7.10 Live CD and want to create separate Partitions.
I have 12G of unallocated space and a 7G XP Home partition.
I wanted to have a shared data NTFS partition and  the above mentioned 3 partitions. Yes I know that you can have only 4 Primary partitions, but I do not understand "logical partition" compared to "primary partitions"
Please help,
Reese

---

### Post by mikewhatever on 2008-03-03
Yes, you can create and mount those partitions using a Live CD, but you don't have too much space for all of them. Anyway, what kind of help do you need? For comparison of primary vs logical, well, here you go [http://www.google.co.il/search?q=primary+vs+logical&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=primary+vs+logical&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by northern lights on 2008-03-03
The most common format of a harddrive has one primary partition followed by an extended partion containing all the logical ones.

Ubuntu can be installed on a logical ext3.

Leave your XP Home primary, and (since you wanna have a separate /home) create two ext3 and one swap.

---

### Post by regbsn on 2008-03-03
So in the 12G unpartitioned space I create "/ home" (ext3), "/" (ext3) and LINUX-SWAP (1 gig)?
If I install Ext2lFS_1_10c.exe in XP Home partition, can I then use "/ home" for my shared data. If I do that, does that protect my data if either OS partition failed or was reinstalled/updated.

I was going to have a fifth partition, with NTFS, until I found out about the 4 partition maximum.

---

### Post by northern lights on 2008-03-03
> **regbsn said:**
> I was going to have a fifth partition, with NTFS, until I found out about the 4 partition maximum.
If you wanted to you could create 19 1gig partitions...

Ext2lFS would make root and /home accessible from Windows. Given that Ubuntu reads and writes to NTFS by default, why wouldn't you create an NTFS partiton for shared files? It might also be enough to not have a separate /home, but only back it up once in a while. This is what I do, as it's not always helpful to leave all old config files when upgrading the distribution.

---

### Post by bodhi.zazen on 2008-03-03
> **regbsn said:**
> So in the 12G unpartitioned space I create "/ home" (ext3), "/" (ext3) and LINUX-SWAP (1 gig)?
If I install Ext2lFS_1_10c.exe in XP Home partition, can I then use "/ home" for my shared data. If I do that, does that protect my data if either OS partition failed or was reinstalled/updated.

I was going to have a fifth partition, with NTFS, until I found out about the 4 partition maximum.

You can only have 4 primary partitions. You can make one an extended partition which then can contain multiple logical partitions.

See this for a brief overview : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by Duck2006 on 2008-03-03
> **bodhi.zazen said:**
> You can only have 4 primary partitions. You can make one an extended partition which then can contain multiple logical partitions.

See this for a brief overview : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

Nice thread on partitioning, lots of good reading.

---

