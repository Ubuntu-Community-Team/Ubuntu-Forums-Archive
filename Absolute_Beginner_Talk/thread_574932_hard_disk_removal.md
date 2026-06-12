---
title: "hard disk removal"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-13
hi,

I am using 7.04. And my hard disk has two partitions (vista in one, Ubuntu in the other). And I want to remove the Ubuntu partition from it and make the two partitions one. How can i do that?

thnx

---

### Post by Pumalite on 2007-10-13
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Boot from it, erase and reformat Ubuntu partition to ntfs
Right click on Vista and choose 'resize partition'
Then restore Vista MBR

---

### Post by limac on 2007-10-13
hi,

I downloaded the gparted live cd 0.3.4-8. I want you to be a bit more specific about how to do it. 

Thnx

---

### Post by limac on 2007-10-13
I can't find anything such as vista or Ubuntu. Can you help me on figuring out what vista and ubuntu is represented by

---

### Post by Pumalite on 2007-10-13
Post:
sudo fdisk -lu
(Usually Vista is in sda1)

---

### Post by nitro_n2o on 2007-10-13
Gparted is pretty easy all what you have to do is delete the partition from the gui interface. Gparted is also available in the LiveCD. Alternatively you can do the same from Vista, look for something like "disk parititioner" I really don't know the exact name or location

** WARNING ** 
If you are dual booting ubuntu and Vista, you'll not be able to boot again after deleting the partition!!! 
because GRUB is responsible for booting and you'll simply delete it and end up with a not bootable box

You should search for: "how to uninstall ubuntu" first, then u can simply delete the partition 

good luck

---

### Post by limac on 2007-10-13
if vista is something like sda2. what is ubuntu usually, sda1?

---

### Post by limac on 2007-10-13
is ubuntu usually sda4 or sda6 or what?

---

### Post by limac on 2007-10-13
another question, what is GRUB? and why can't I boot if I delete a partition? If I accidentaly delete GRUB, what should I do? How can I solve that problem?

---

### Post by Pumalite on 2007-10-13
Windows runs in sda1, a primary partition; Ubuntu in sda2 to sda5, or 6 or 7, all usually extended/logical partitions.
(that is the usual setup in a bought computer with XP or Vista installed. Laptops have a small 'recovery partition' at the beginning of the drive.)

---

### Post by limac on 2007-10-13
are u sure because when I check in windows it says that total size = 59.69gb and 21.68gb used. and in this in sda2 it says the same thing. And sda1 says 1.46 gib

---

### Post by Pumalite on 2007-10-13
Then you have a laptop and sda1 is the 'recovery partition' and Windblows is in sda2.

---

### Post by limac on 2007-10-13
yeah so which one of the sda's in my laptop do u think is ubuntu 7.04?

---

### Post by Pumalite on 2007-10-13
The rest.

---

### Post by limac on 2007-10-13
I found out two sda's. One says sda3 ext3 that has 11.42gb volume in total. And another one is sda6 which says ext3 3.98gb. Now when I open ubuntu and go to disk usage analyzer it says 3.89gb free and that matches  sda6. But if I open Computer in ubuntu, it says 11.42 total volume. now which one should I go with. And after I get the partition I want to remove, what will be the next step. please explain in detail.

---

### Post by mysurface on 2007-10-13
> **limac said:**
> is ubuntu usually sda4 or sda6 or what?

sudo fdisk -l

it clearly shows you what sda# point to what filesystem, you may get a clue on your partition's info

---

### Post by limac on 2007-10-14
well yeah it is helpful, but there are two sda#'s that show linux under system so to delete the ubuntu partiton from the hard disk what shoul I do?

---

### Post by Pumalite on 2007-10-14
Post the output of:
sudo fdisk -lu

---

### Post by limac on 2007-10-14
here's the reply:
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074048   121954907    59440430    7  HPFS/NTFS
/dev/sda3       121965480   145918394    11976457+  83  Linux
/dev/sda4       145918395   156296384     5188995    5  Extended
/dev/sda5       154770273   156296384      763056   82  Linux swap / Solaris
/dev/sda6   *   145918521   154272194     4176837   83  Linux
/dev/sda7       154272258   154770209      248976   82  Linux swap / Solaris

Partition table entries are not in disk order

Partition table entries are not in disk order     :-({|=

---

### Post by Pumalite on 2007-10-14
Sda3 to sda7 are Linux. I don't know why you have 2 /swaps. Two Linux installed?

---

### Post by limac on 2007-10-14
what about sda6?

---

