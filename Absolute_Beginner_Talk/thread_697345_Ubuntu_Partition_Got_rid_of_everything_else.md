---
title: "Ubuntu Partition Got rid of everything else?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by ThunderPanda on 2008-02-15
I just installed Ubuntu, but I have a problem. When it first asks you to make a partition, it has you select how big the partition was supposed to be. I assumed it would just add a partition to the existing one, using the free space that is there. Also, it told me I would be able to restore everything if I didnt like it? Anyway, I dont like it, because now I cant access anything that used to be on that harddrive, not from Ubuntu and not even from windows. So I was wondering if and how I can restore the hard drive to how it was. It is on a second hard drive without vital system files, so thats why it hasnt resulted in catastrophic failure. Any help would be appreciated.

---

### Post by mikewhatever on 2008-02-15
Please open Applications>Accessories>Terminal and post the output of the following command: > sudo fdisk -lu

---

### Post by ThunderPanda on 2008-02-15
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x064f064e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    78252614    39126276    7  HPFS/NTFS
/dev/hda2        78252615   320159384   120953385    f  W95 Ext'd (LBA)
/dev/hda5        78252678   320159384   120953353+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08d48043

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       458977050   488392064    14707507+  83  Linux

---

### Post by ThunderPanda on 2008-02-15
Also, I have two hard drives, the first one had two windows partitions, and then I installed Ubuntu on the second Hard Drive, and tried to make a second partition on it, if any of that helps.

---

### Post by mikewhatever on 2008-02-17
It looks like /dev/sda, your second HDD has only one Linux partition, so you must have formatted all of it. Unless there are more partitions, all data that used to be there is lost. You can remove Ubuntu following one of the options from the [uninstall page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"). I'd advise windows recovery console, if you have the CD, mbrfix.exe or supergrub. If you ever venture to install Ubuntu or another OS again do some research first, A google search for 'ubuntu installation' would have turned up a number of excellent guides with pictures and explanations of how to do it right. Good Luck.

---

