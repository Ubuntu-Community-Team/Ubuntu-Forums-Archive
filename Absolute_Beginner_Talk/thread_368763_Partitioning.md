---
title: "Partitioning"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2007-02-23
Been searching the forums on how to make a **swap parition** and **converting my old NTFS partition into an ext3**. 

Couldn't find any specific answer that seemed safe. However, I did do **sudo mke2fs -j /dev/sda5** and now there is nothing left on it, which is what I want. I made a backup so basically I can mess about as much as I want, still I'm just a noobie. 

What I want, or think would be the best, is to first of creating a swap partition out of my old NTFS partition which is 112gb, then make the rest of it as an ext3. Could anyone help me out on doing this?

**free**:
[HTML]
             total       used       free     shared    buffers     cached
Mem:       1034852     340664     694188          0       6384     132812
-/+ buffers/cache:     201468     833384
Swap:            0          0          0[/HTML]

---

### Post by taurus on 2007-02-23
Use gparted to resize that partition and format the smaller one as swap and the left over space to ext3.

---

### Post by urk_nono on 2007-02-23
> **taurus said:**
> Use gparted to resize that partition and format the smaller one as swap and the left over space to ext3.

I know I prolly should use gparted, however I'm eager to learn the commands by using fdisk.

---

