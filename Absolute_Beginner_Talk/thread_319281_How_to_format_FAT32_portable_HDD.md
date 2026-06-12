---
title: "How to format FAT32 portable HDD"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by feap on 2006-12-15
I just bought a HyperDrive SPACE portable HDD USB casing and installed a Samsung SpinPoint M60 (model # HM160JC) 160GB HDD into it. This is a drive that's used to dump camera RAW files directly from a CF card. I will also use it as a portable HDD for movie files, mp3s, etc.

The disk shows up in administration/disks but the format button is greyed out. The disk has been already FAT32 formatted by Hyperdrive SPACE but I need to do it "properly" in Ubuntu. This is because Hyperdrive SPACE only formats it to 128GB and it shows only 8GB free in Ubuntu even though it's empty. Hopefully formatting in Ubuntu will fix these problems.

The best manual guide was [http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive](http://wiki.linuxquestions.org/wiki/Add_a_new_hard_drive) but it stops short of explaining how to actually format the drive. I've checked the first few google hits for mkfs and mkdosfs but it's not really helpful for a n00b.

I have partitioned the drive with just one partition and won't need more than that. The to-be-formatted drive is /dev/sbd.

So the question is: how do I partition and format a 160GB USB external HDD to FAT32?

I need to format it with FAT32 due to the casing so please don't suggest ext3 or anything other than FAT32.

---

### Post by feap on 2006-12-15
I installed gparted which doesn't work, either. After I unmounted the HDD and went to format to/FAT32 and click on apply, gparted starts the formatting but I get an extremely helpful error screen "error while formatting filesystem..." after a few seconds. Ubuntu then opens File Browser to the drive which hasn't been touched - it's in the same 8.4GB free state as earlier.

---

### Post by bodhi.zazen on 2006-12-15
Unmount the device

Then, in a terminal:```
sudo mkfs.vfat -n <label_name> <device>
```

You can also use gparted.

Gparted documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

See here for other partitioning options: [how to partition](http://www.ubuntuforums.org/showthread.php?&t=282018)

See here for a script I wrote that will do this for you:

[Format removable devices](http://www.ubuntuforums.org/showthread.php?&t=302724)

---

### Post by feap on 2006-12-15
Yay that worked! I guess I did something wrong in gparted, but the terminal command worked. Thank you so much for the quick reply! This forum once again has proven how good Ubuntu support is :)

For some reason it only made a 128GB partition. I might have to make 2 partitions to get access to the entire 160GBs.

---

### Post by bodhi.zazen on 2006-12-15
Some of the drive space (5%) may be taken up by the file system itself although I am no sure about FAT.

  32 Gb seems excessive. Not all Gb are equal :)

---

