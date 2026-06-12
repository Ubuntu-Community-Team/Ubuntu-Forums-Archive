---
title: "USB flash memory/stick became &quot;Write only&quot; !!"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Motorhead Kaze on 2008-02-29
I bought a USB flash memory stick and used it for a couple days, right out of the box, no hassles, and was able to save and delete files.  Then a couple days later I get a message telling me the stick is write only and I can't delete the old files.

I am going to assume for now that going back and forth between XP and Ubuntu screwed it up.  How do I unscrew it?  Rather, FIX it?

Thanks.

---

### Post by taurus on 2008-02-29
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
mount
```

---

### Post by gpilkay on 2008-02-29
The only time this happened to me, I went to XP (sorry!) and when I had the thumb drive in, I right clicked it, chose properties, chose tools, went to error checking, clicked Check Now, and clicked the 'automatically fix file system errors' box.  That cleaned it up for me.

---

### Post by glennric on 2008-02-29
You can check a vfat drive from linux too.  Type
```
fsck /dev/???
```
Where ??? is the partitions device name.  You can get this from "sudo fdisk -l"

---

### Post by Motorhead Kaze on 2008-03-02
Sorry I took a bit of time to respond, here is the output:

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000080e3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13021   104591151    7  HPFS/NTFS
/dev/hda2           38254       38913     5301450    5  Extended
/dev/hda3           13022       38253   202676040   83  Linux
/dev/hda5           38584       38913     2650693+  82  Linux swap / Solaris
/dev/hda6           38254       38583     2650662   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6441e136

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdb: 2014 MB, 2014838784 bytes
64 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         976     1967489+   6  FAT16

What does this tell you?

---

### Post by Motorhead Kaze on 2008-03-04
Glenric, that didn't fix it for me.  Any idea why? I would prefer to fix problems that come up in Ubuntu, IN Ubuntu.  Any further advice?

Gpilkay, yes that worked.  I would really rather know how to fix the problem IN Ubuntu, so I don't have to restart my computer each time this happens, but I did exactly what you said, and it worked great.  Xp fixed my problem.

Taurus, you asked for that info but?  Where'd ya go?

---

### Post by gpilkay on 2008-03-04
Great, glad it worked!  I'm the black sheep of the forum, I use both XP and Ubuntu on both my systems, and I like BOTH.  Ubuntu is far more secure, faster, and to be blunt, easier for me to use.  XP handles USB drives and printers better and is essential for government and job sites.  They both have their uses, and while they can sub for each other, they don't do it well.

I figure, use whatever works best for what you want.  Glad I was able to help!

For future trouble avoidance, always hit the 'unmount volume' before removing the drive and if it says 'do you want to empty trash?' hit yes, it's a bit of a bug in the system that'll leave behind a folder labeled .trash with the files you thought you deleted if you don't.

---

### Post by Motorhead Kaze on 2008-03-05
Yeah, I noticed that.  Printing in good quality in xp is double time that of printing in Ubuntu, even in draft mode.  I too need to at least OWN legal copy of MSOffice, I am a translator.  In fact, I do my work in Open Office and save as .doc files -- what a sweet feature that is!  

It is true though, things that were made for XP work well with it.  My scanner is one of the main reasons why I kept XP too.  There is no Linux driver for it, and I don't know how to make them.  

Nice pointer about the unmount command.  I learned that when Ubuntu yelled at me about it.  hahaha.

Take care and thanks again.

---

