---
title: "[SOLVED] Newly formatted/mounted hard drive question"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-04-06
As my first time doing this...

I just formatted a 120GB HD with ext3 and mouted it, with a mount point.

When I go into the file system, under the mount point directory, it says only 111.4 GB.

I used the command to use only 1% of reserve space.
 sudo tune2fs -m 1 /dev/sda

This drive did contain MS Windows Home Server, which is based on Win 2003... not sure what the it would have been... NTFS possibly.  I believe there was only one partition on it.

Why would I only 111 BG... missing 19 GB?

---

### Post by softtower on 2008-04-06
Your drive is not 120GB, your hard drive really has only $111GB. Manufacturers always lie to us about their drive sizes. Normally they get away with it by defining their own meaning of "Gigabyte". 

Normally  it goes like this:

1KB is 1024 bytes
1MB is 1024KB
1GB is 1024MB

Therefore, 1GB is (1024*1024*1024) is 1,073,741,824 bytes

But hard drive manufacturers, to make themselves look better and to inflate sizes of their drives, "think" that one GB is only 1,000,000,000 bytes, hence the difference.
You have 111GB hard drive, Ubuntu is right. :-)

---

### Post by Rocket2DMn on 2008-04-06
> **softtower said:**
> Your drive is not 120GB, manufacturers always lie to us about that. Normally it goes like this:
1KB is 1024 bytes
1MB is 1024KB
1GB is 1024MB

Therefore, 1GB is (1024*1024*1024) is 1,073,741,824 bytes

But hard drive manufacturers, to make themselves look better, and to inflate sizes of their drives, count one GB as 1,000,000,000 bytes, hence the difference.

Indeed.  Simply stated, 1GB = 2^30 bytes (it's a binary thing), whereas manufacturers call a GB 10^9 bytes.  The ext3 filesystem also has a high overhead, so you can lose a few GB to that as well.

---

### Post by BlizzofOZ on 2008-04-06
Thanks... I know I've seen that on Windows systems, just didn't realize it was that excessive.

Thanks!

---

