---
title: "error starting ubuntu"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by venomasphyx on 2008-02-08
when I start my system it forces an fsck - gets about 40% through, and then craps out - tells me I need to do a manual check, so I start one, and this happens repeatedly:

Buffer I/O error on device sda1, logical block [...]. Error reading block [...] (attempt to read block frofile system resulted in short read) while reading indirect block of inode [...]. Ignore error ?

Force rewrite?

Inode [...], i_blocks is [...], should be [...]. Fix?

[nnn.nnnnnn] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[nnn.nnnnnn] ata1.00: (BMDMA stat 0x25)
[nnn.nnnnnn] ata1.00: cmd c8/00:08:47:16:c7/00:00:00:00:00/e3 tag 0 cdb 0x0 data 4096 in [repeats]

sometimes a "revalidation failed (errno=-2)" will pop up in the mix. 

is there anything I can do to fix this without having to reinstll ubuntu? Or anything to prevent this from happening if I do have to reinstall?

---

### Post by overdrank on 2008-02-08
> **venomasphyx said:**
> when I start my system it forces an fsck - gets about 40% through, and then craps out - tells me I need to do a manual check, so I start one, and this happens repeatedly:

Buffer I/O error on device sda1, logical block [...]. Error reading block [...] (attempt to read block frofile system resulted in short read) while reading indirect block of inode [...]. Ignore error ?

Force rewrite?

Inode [...], i_blocks is [...], should be [...]. Fix?

[nnn.nnnnnn] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[nnn.nnnnnn] ata1.00: (BMDMA stat 0x25)
[nnn.nnnnnn] ata1.00: cmd c8/00:08:47:16:c7/00:00:00:00:00/e3 tag 0 cdb 0x0 data 4096 in [repeats]

sometimes a "revalidation failed (errno=-2)" will pop up in the mix. 

is there anything I can do to fix this without having to reinstll ubuntu? Or anything to prevent this from happening if I do have to reinstall?

HI and welcome, have you tried to run fsck from the live cd, it has helped me a few times.

---

