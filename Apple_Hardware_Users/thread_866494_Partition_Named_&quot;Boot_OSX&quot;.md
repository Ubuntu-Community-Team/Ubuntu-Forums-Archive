---
title: "Partition Named &quot;Boot OSX&quot;?"
date: 2008-07-21
forum: Apple Hardware Users
---

### Post by kdb424 on 2008-07-21
After installing ubuntu on my Macbook Pro, I had 2 extra partitions. "Partition 3", and "Boot OSX". When I use rEFIt to boot, I need to boot from the "Boot OSX" partition to get into Ubuntu, but when I boot "Partition 3", it won't boot. All of the data for ubuntu is installed on the "Partition 3", but will only boot from "Boot OSX" Does that mean that the grub boot loader is on it's own partition? How can I make it so that there are only 3 partitions?

It is currently

(hd0,1) EFI
(hd0,2) Mac
(hd0,3) Ubuntu (AKA "Partition 3")
(hd0,4) Some weird hidden files (AKA "Boot OSX")

I want that last one gone, because it gets annoying in rEFIt.

The last problem is that I want to partition my hard drive, but my mac partition won't partition any more because it needs to be hfs+ Journaled it tells me, but it already is exactly that. Any ideas? BTW, I don't have an external so I can't back my stuff up, or make it one partition and start over.

edit: I am sure that the grub boot loader is on partition 3 now.

---

