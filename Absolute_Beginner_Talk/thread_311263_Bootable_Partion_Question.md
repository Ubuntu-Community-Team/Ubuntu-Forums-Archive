---
title: "Bootable Partion Question"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by i.am.canadian on 2006-12-02
I'm trying to prepare my HD for my upcoming Ubuntu install.  I am using PartitionMagic (PM) to create some space out of my NTFS partition, but I had a two questions.

First, when I try and partition my HD in such a way that my free space is at the beginning of the HD, PM tells me that my Windows partiton is going to start beyond the 1024 cylinder threshold and therefore it will not be bootable.  Is this true? Or would GRUB deal with this?

Second, my understanding is that ext3 partitions cannot be resized from the beginning, only from the end (this is why I want to put them before my NTFS partition).  Again, is this something I need to be concerned about if I intend to eventually remove Windows entirely and want to use my entire HD for linux.

That's all for now, I really appreciate any input that anyone has.  Cheers everyone.

---

### Post by smoker on 2006-12-02
not sure about partition magic, never used it, but i use 'gparted' boot disk to partition, it runs from cd therefore outwith windows or any other os, so doesn't have the constraints of having to juggle partitions while fighting with an operating system.

if you want to try the gparted boot disc you can download an iso from sourceforge.net.

---

