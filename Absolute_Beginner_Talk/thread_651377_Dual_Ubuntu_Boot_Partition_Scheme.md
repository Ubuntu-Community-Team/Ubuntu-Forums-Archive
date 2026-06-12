---
title: "Dual Ubuntu Boot Partition Scheme"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by hgodling on 2007-12-27
I'm trying to figure out a partitioning scheme so that I can dual boot 32-bit and 64-bit Ubuntu.  I know that this is not the "proper" way of doing this but i think this is best for me and will allow future flexibility. I am think about using the following scheme.

hda1 (8 yr old 20GB IDE HD)
0.1GB - /boot - 64-bit
0.1GB - /boot - 32-bit
2GB - / - 32-bit
1GB - / - 64-bit
1GB - /var - 64-bit
2GB - /tmp
1GB - swap
12.8GB - /archive

hda2 (160GB SATA HD)
1.5GB - swap
10 GB - /usr - 64-bit
10 GB - /usr - 32-bit
158.5GB - /home

I wanted to make sure that I'm not overlooking anything and that this scheme actually possible.

Thank You

---

### Post by jken146 on 2007-12-27
You don't need that much swap (more than 1G in total is a waste of space).  I would also recommend increasing the sizes of those / partitions if you can.

---

### Post by LinuxIsInnovation on 2007-12-27
Btw, going off topic, but do you want to dual boot 32 and 64 bit versions of the same distro and version.. If so, theres no need at all.. Just go for the 64-bit one.

---

