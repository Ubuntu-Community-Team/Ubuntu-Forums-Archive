---
title: "Nautilus ntfs-3g fades to dim, slow ..."
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-03
When I use Nautilus browser to browse to my NTFS /dev/sda1 partition, Nautilus fads to dim and back and runs very slow.  Nautilus runs like it is supposed to run for ext2 partitions.

Any one have a solution?

Thanks

Carl

---

### Post by jiminycricket on 2007-06-03
When you say the window dims, I guess you're running Compiz or Beryl?  NTFS-3g uses a lot of CPU b/c it's not a kernel module but a FUSE program, and is not fully optimized yet, so a future release might speed up.  Have you also tried chkdsk and defragmenting on the Windows side?

---

### Post by cwmoser on 2007-06-03
I had read a post suggesting to chkdsk, increase free space, and to defrag.
I am running Beryl.

Carl


> **jiminycricket said:**
> When you say the window dims, I guess you're running Compiz or Beryl?  NTFS-3g uses a lot of CPU b/c it's not a kernel module but a FUSE program, and is not fully optimized yet, so a future release might speed up.  Have you also tried chkdsk and defragmenting on the Windows side?

---

