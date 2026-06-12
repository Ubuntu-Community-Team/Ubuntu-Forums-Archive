---
title: "LVM and filesystem type"
date: 2008-11-14
forum: Arch and derivatives
---

### Post by medic2000 on 2008-11-14
I am gonnoa use LVM on my next installation what type of filesystem do you suggest?

---

### Post by mips on 2008-11-14
Do you ever intend to 'shrink' a filesystem? If your answer is 'yes' then stick with ext2/3, reiserfs.

If you don't intend to ever shrink a filesystem look into jfs&xfs.

The last time I did a LVM setup (which was cool) I used XFS as i had no intention to ever shrink a filesystem/partition.

Next time I reinstall Arch I will consider putting my 500/250&160GB drives into a LVM.

[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)




.

---

### Post by dentharg on 2008-11-14
XFS can fry data.
But you should treat LVM the same as any other partition and choose an FS according to your designation. Eg. when this LVM is stored mostly for source code, etc. Reiserfs is way to go. For video XFS is the best. EXT3 is excellent as generic purpose FS.

---

### Post by medic2000 on 2008-11-15
> **mips said:**
> Do you ever intend to 'shrink' a filesystem? If your answer is 'yes' then stick with ext2/3, reiserfs.

If you don't intend to ever shrink a filesystem look into jfs&xfs.

The last time I did a LVM setup (which was cool) I used XFS as i had no intention to ever shrink a filesystem/partition.

Next time I reinstall Arch I will consider putting my 500/250&160GB drives into a LVM.

[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)




.

What does this "shrink" means. Can you give me an example?

---

### Post by mevem on 2008-11-15
> **medic2000 said:**
> What does this "shrink" means. Can you give me an example?Shrink is to make something smaller.

---

### Post by mips on 2008-11-15
> **medic2000 said:**
> What does this "shrink" means. Can you give me an example?

To make something smaller. Do you think you will ever make one of your partitions on the LVM smaller.

With JFS/XFS you can only make a partition bigger, not smaller.

---

### Post by medic2000 on 2008-11-15
Hmmm it is quite disadvantage for me.

---

