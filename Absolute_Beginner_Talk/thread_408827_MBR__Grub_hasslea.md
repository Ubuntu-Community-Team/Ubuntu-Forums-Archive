---
title: "MBR / Grub hasslea"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by oomingmak on 2007-04-13
I've just about been able to get my head around this sda sdb, hda hdb business for hard drives. However, as if this wasn't as cryptic enough, when you try to specify where grub should be loaded, you get a totally different name format of "Hd0" displayed with absolutely no other choices and no means of knowing what the hell drive grub is going to be put on.

Is there some kind of standard relationship between these two naming schemes? and is there are reason why one arcane abbreviation system is not enough (or are they just deliberately trying to torment newbies?). ](*,) 

On one recent install, I tried leaving it at the default value but it ended up destroying the MBR on my Windows drive (which Ubuntu seems to do with such regularity that I'm beginning to think that it enjoys it). This will invariably be followed by an error 17 (rendering neither Windows nor Ubuntu bootable).

I've got wise to the installer's antics these days (having been *severely *burned in the past) and so nowadays I always image my Windows disk before I let Ubuntu anywhere near my system, but I'd still like to be able to make sense of the hd0 stuff as I have no idea how it relates to sda sdb and my hit and miss guessing approach is not really getting me very far.

Thanks for any explanations / advice.

---

### Post by lamalex on 2007-04-13
it's (hdX,Y) where is the disk number, starting from 0, and Y is the partition number, starting from 0. it has nothing to do with the hda sda business.

---

### Post by oomingmak on 2007-04-13
OK, But where does it start numbering from?

Is hd0 a cd drive? an ide drive? the first SATA drive?

---

### Post by lamalex on 2007-04-13
do you have both sata and ide hard drives? I've only ever had sata or ide, not both and either way the primary drive was 0 and it went from there

---

