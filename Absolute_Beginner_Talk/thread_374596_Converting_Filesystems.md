---
title: "Converting Filesystems"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by sushii. on 2007-03-02
Heyy, I just have a quick question. When I was running the Ubuntu installer, I somehow converted my Windows NTFS partition to swap space. Is there any way to get it back to NTFS without losing my data? Thanks.

---

### Post by taurus on 2007-03-02
Use gparted from the LiveCD (System -> Administration) and tag it back as ntfs and see if all your files are still on it.

---

### Post by sushii. on 2007-03-02
I tried doing that but it wouldn't let me format to NTFS. I went to Partition > format to > ntfs (which i couldn't select). Is this correct? And do I have to use the Live CD? Thanks.

---

### Post by taurus on 2007-03-02
Yes, you have to use the LiveCD unless you unmount the swap partition first since gparted won't work on a mounted partition.

And I would strongly recommend you don't boot into Ubuntu anymore since it will write stuff to the swap and it makes it harder to recover your stuff from it.

---

### Post by sushii. on 2007-03-02
Okay, well I unmounted it cuz I can't seem to get the live CD working.. and I don't want to go through all the trouble of fixing that bla bla bla... but i still can't get it to NTFS. Any suggestions? Sorry if I suck at following your instructions. I'm a total noob to linux.. this is all new to me!

---

### Post by taurus on 2007-03-02
Are you sure you have unmounted the swap partition?  What's the output of these two commands from a terminal?

```
free 
sudo fdisk -l
```

---

### Post by sushii. on 2007-03-02
free:
```
             total       used       free     shared    buffers     cached
Mem:        450436     414864      35572          0       6692     154064
-/+ buffers/cache:     254108     196328
Swap:       152608      17608     135000

```
fdisk:
```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       15278   122720503+  83  Linux
/dev/hda2           15298       19457    33407640    b  W95 FAT32
Partition 2 does not end on cylinder boundary.
/dev/hda3           15279       15297      152617+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

EDIT: Oh yeah, BTW, I changed it to FAT32 to see if i could mount it.. but i think it deleted everything. :(

---

