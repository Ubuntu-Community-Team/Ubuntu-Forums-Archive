---
title: "Need help with mapping in grub"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by aswells on 2006-12-09
I am having trouble with the mapping feature within grub. I have a ext3 partition, hda1 (hd0,0) for grub, and a NTFS partition hda2 (hd0,1). I am trying to swap them around so that the ext3 partition is (hd0,1) and NTFS is (hd0,0). I have tried using a knoppix cd as well as a ubuntu live cd. These are the commands I tried.

```
sudo grub
map (hd0,1) (hd0,0)
map (hd0,0) (hd0,1)
```

that didnt seem to do it, so I tried

```
sudo grub
map (hd1) (hd0)
map (hd0) (hd1)
```

same result, nada. I thought maybe that I couldnt make a drive to a place that was already used, so I tried:
```
sudo grub
map (hd0,0) (hd0,7)
map (hd0,1) (hd0,0)
map (hd0,7) (hdo,1)
```

none of these seemed to have any effect with a
```
sudo fdisk -l
```

Any ideas or input would be greatly appreciated.

---

### Post by lha on 2006-12-09
I don't think it is possible to use map after os has loaded. Even if it was, the results would be quite unpleasant. In addition, map tells the bios to show eg. hda as hdb and vice versa. It cannot swap partitions.

---

