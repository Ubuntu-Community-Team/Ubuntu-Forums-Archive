---
title: "Format partitiion after installation"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by stena on 2008-02-24
I successfully (I hope :)) installed Ubuntu Gutsy on my ThinkPad X41 Laptop, keeping XP as well for dual boot. Everything works fine so far, so I decided to give Ubuntu more space.

Out of 60 GB on HDD, I have 15 GB on C: (where XP installation is), another 35 GB on D: (NTFS, used for storage under XP) and 10 GB /ext3 for Ubuntu (500MB for SWAP also, of course).

Now, I made all necessary copies and have all data I need from XP on C: disk, and D: partition, which is still NTFS is empty and ready to be formated in ext3 for UBUNTU (probably as /home).

Can you please tell me how to do it?

Thank you very much in advance guys.

Regards,
stena

---

### Post by spiderbatdad on 2008-02-24
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bazzawill on 2008-02-24
Add the application gparted from the package manager it will guide you through deleteing your old partitions and creating a new ext3 partition. Gparted can be a bit slow but is much more user friendly than command line options

---

### Post by spiderbatdad on 2008-02-24
> **bazzawill said:**
> Add the application gparted from the package manager it will guide you through deleteing your old partitions and creating a new ext3 partition. Gparted can be a bit slow but is much more user friendly than command line options

Not necessary. The live cd uses qtparted. If you want to use gparted, as the guide I linked above suggests, you will want a live cd of gparted, as the disk must be unmounted during the partitioning.

---

### Post by stena on 2008-02-24
Uf, thanks, but there is a small problem. I have no CD drive on my ThinkPad, I used Unetbootin and did the whole installation from internet.

Will GParted do the job in that case?

Thanks again,
stena

---

