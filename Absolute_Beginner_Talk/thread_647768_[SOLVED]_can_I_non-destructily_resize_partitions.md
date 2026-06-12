---
title: "[SOLVED] can I non-destructily resize partitions?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2007-12-22
I triple booted my macbook then my windows stopped working and I figure I don't really need it so can I delete my windows and make my ubuntu bigger without earasing my ubuntu data?

---

### Post by logos34 on 2007-12-22
Use the Gparted live cd to grow ubuntu.

---

### Post by chris200x9 on 2007-12-22
ok are you sure it will keep all my settings and everything.

---

### Post by logos34 on 2007-12-22
yes, if you do it correctly.

sounds like osx is first partition, [empty--formally windows], ubuntu root, swap.

so you'll be expanding the ubuntu root to left.  The partition # stays the same so grub should contunue to boot ok.  

Post 

sudo fdisk -l

and/or a screenshot of your disk layout

gksudo gparted

---

### Post by chris200x9 on 2007-12-22
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2              26       10467    83868436   af  Unknown
/dev/sda3   *       12689       14594    15304112    7  HPFS/NTFS
/dev/sda4           10467       12688    17842773+  ef  EFI (FAT-12/16/32)

Partition table entries are not in disk order

---

### Post by logos34 on 2007-12-22
ok, it's not what I was expecting, you'll need to fill me in.  

sda1 - mac recovery/utilty?
sda2 - mac root?
sda4 - mac swap?
sda3 - obviously windows

where's ubuntu?

---

### Post by chris200x9 on 2007-12-22
I know I can't tell by that either but w/e I'll figure it out all I needed to know was it can non-destructivly do it thanx :)

---

