---
title: "deleting file system"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-08-07
I tried to put ipodlinux on my ipod mini.  Later I found out that my ipod wasnt supported.  I had created a ext3 file system (before that I had created a VFAT filesystem but tha works fine)  Is there a way I can delete the filesytem without touching my VFAT filesystem?
EDIT:I found out it was a ext2 filesystem

---

### Post by wombat20 on 2006-08-07
I guess you would need a partitioning program like GParted or PartitionMagic the latter being non-free.

GParted is in the repositories or on an Ubuntu live cd.

---

### Post by greyash99 on 2006-08-07
thanks I'll try that

---

### Post by greyash99 on 2006-08-07
I can't use synaptic because clamscan has unresolved dependencies. I don;t know how to resolve them either so I'm kind of stuck.

---

### Post by cantormath on 2006-08-07
> **greyash99 said:**
> I can't use synaptic because clamscan has unresolved dependencies. I don;t know how to resolve them either so I'm kind of stuck.

uninstall clamscan or open synaptic and fix broken packages.

---

### Post by greyash99 on 2006-08-07
ok cool now synaptic and clamscan works so I can try gparted
gparted says the ipod is unallocated. does that mean it wont work?

---

