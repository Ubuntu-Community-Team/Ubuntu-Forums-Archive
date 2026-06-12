---
title: "DVD Won't mount"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by panther_sn on 2008-03-20
I recently wrote a DVD in K3B, then reformatted PC, now still using Gutsy and K3B I cannot load the DVD, no hardware has changed so I am not quite sure.  The message I get when I try to load it is 
```
mount: wrong fs type, bad option, bad superblock on /dev/scd0,

       missing codepage or helper program, or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so


```and when I do  dmesg | tail i get


```
taz@taz-desktop:~$ dmesg | tail
[15058.041294] sd 0:0:0:0: [sda] Write Protect is off
[15058.041302] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[15058.041725] attempt to access beyond end of device
[15058.041732] sr0: rw=0, want=68, limit=4
[15058.042206] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[15058.042474] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[15058.042925] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[15058.063902] sd 0:0:0:0: [sda] Write Protect is off
[15058.063912] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[15058.067601] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Any ideas How I can fix this problem

---

### Post by billgoldberg on 2008-03-20
I have no idea, but you might want to repost your question in the correct forum, it might get you more responses.

---

### Post by panther_sn on 2008-03-22
Whichj Forum would u suggest?

---

