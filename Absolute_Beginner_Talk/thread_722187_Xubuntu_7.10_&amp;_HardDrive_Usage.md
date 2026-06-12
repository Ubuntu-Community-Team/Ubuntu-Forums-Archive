---
title: "Xubuntu 7.10 &amp; HardDrive Usage??"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by mltom on 2008-03-12
I have a 2 pc environment.

1) installed Xubuntu 7.10 & it works great. Then I noticed it was only using 34g of my 400g hd.

2) downloaded 'gparted', from OSD folks, onto my primary XP pc but the cd burner seems not to be working for a 'image burn'.(Roxio)

3) purchased 'PartedMagic', from the OSD guys, but it has a problem booting up.

4) did a re-install using my 'Xubuntu LiveCD', & choose 'Entire Disk LVM' as my install option. It took much longer than my first install but still only uses 34g.

Any ideas?
tks
tom

---

### Post by NightwishFan on 2008-03-12
Post the output of this from a terminal:
```
sudo fdisk -l
```

---

### Post by jan quark on 2008-03-12
please post the result of 

```
sudo fdisk -l
```

edit
I am blind sry for double post

---

### Post by mltom on 2008-03-13
Disk /dev/hde: 34.2 GB, 34219745280 bytes
255 heads, 63 sectors/track, 4160 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        4114    33045673+  83  Linux
/dev/hde2            4115        4160      369495    5  Extended
/dev/hde5            4115        4160      369463+  82  Linux swap / Solaris

See I have much more disk space.
tks
tom

---

