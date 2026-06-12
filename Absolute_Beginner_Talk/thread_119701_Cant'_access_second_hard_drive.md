---
title: "Cant' access second hard drive"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by damianmann on 2006-01-20
It's there. but notice the next to last line:




Disk /dev/hda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 2436 19567138+ 83 Linux
/dev/hda2 2437 2491 441787+ 5 Extended
/dev/hda5 2437 2491 441756 82 Linux swap / Solaris

Disk /dev/hdb: 4223 MB, 4223729664 bytes
128 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 1023 4124704+ 6 FAT16
**Partition 1 has different physical/logical endings:**
phys=(1021, 127, 63) logical=(1022, 127, 63)





So, what's that about?

---

### Post by xmastree on 2006-01-20
Is there anything on it? If not, try running gparted or qtparted, or some other partitioning tool and start over.

You say you can't access it, what happens if you try to mount it?

---

