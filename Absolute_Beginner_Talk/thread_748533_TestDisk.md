---
title: "TestDisk"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by noskillz on 2008-04-07
Anyone familiar with TestDisk? I re-wrote the partition with windows on in and used testdisk to recover the partition. The NTFS file shows when analyzed by TestDisk:

 1 P HPFS - NTFS              6   0  1 11546 254 63  185406165
 2 * Linux                11547   0  1 11951 254 63    6506325
 3 E extended             11952   0  1 11977 254 63     417690
 5 L Linux Swap           11952   1  1 11977 254 63     

When I boot up I get the option to choose windows xp (because i added it to the GRUB list) my menu.lst looks like this:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8c163af0-2264-4a1b-b75f-43dd6d2b165a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8c163af0-2264-4a1b-b75f-43dd6d2b165a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title           Windows XP
rootnoverify           (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
makeactive
boot

Any suggestions on how to get the partition 1 (ntfs) to boot up?

---

### Post by Duck2006 on 2008-04-07
Try from this,
> 
title Windows XP
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
makeactive
boot

To this.

title Windows XP
root (hd0,0)
makeactive
chainloader +1

---

### Post by noskillz on 2008-04-07
> **Duck2006 said:**
> Try from this,


To this.

title Windows XP
root (hd0,0)
makeactive
chainloader +1

okay, when I did that it went to a blank screen saying "starting up..." for about 5 minutes and then I rebooted into Ubuntu. First time I have been able to get past the OS selection screen so that may be a good thing, but on the the flip side it went nowhere. Thoughts?

---

### Post by Duck2006 on 2008-04-07
From the terminal type

fdisk -l

and post the output hear.

---

### Post by noskillz on 2008-04-07
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           7       11547    92703082+   7  HPFS/NTFS
/dev/sda2           11548       11952     3253162+  83  Linux
/dev/sda3           11953       11978      208845    5  Extended
/dev/sda5           11953       11978      208813+  82  Linux swap / Solaris

That is encouraging...last night when I did this the first partition NTSF was gone completely, Looks like I restored it. So what is my next move?

---

### Post by forestpixie on 2008-04-07
```
sudo fdisk -l 
```

---

### Post by noskillz on 2008-04-07
> **forestpixie said:**
> ```
sudo fdisk -l 
```

The above was the results of that.

---

### Post by Duck2006 on 2008-04-07
> **noskillz said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           7       11547    92703082+   7  HPFS/NTFS
/dev/sda2           11548       11952     3253162+  83  Linux
/dev/sda3           11953       11978      208845    5  Extended
/dev/sda5           11953       11978      208813+  82  Linux swap / Solaris

That is encouraging...last night when I did this the first partition NTSF was gone completely, Looks like I restored it. So what is my next move?

Sounds like some thing in your first partition is corrupted. This is the grub page and may help.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by noskillz on 2008-04-07
I don't see where it helps with my problem.

---

### Post by Duck2006 on 2008-04-07
You can try super grub live cd.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by noskillz on 2008-04-07
I don't get how restoring grub will repair a corrupted windows partition.

---

### Post by Duck2006 on 2008-04-07
You may have to save your data on the partition and reinstall win again. Can you see the partition from linux?

---

### Post by noskillz on 2008-04-07
I can see the windows partition when I'm in linux in testdisk and through fdisk -l. The problem is I can't boot into windows. I can also use testdisk to see the files listed in that partition, so I think I've recovered them. I just don't know what to do from here.

---

### Post by louieb on 2008-04-07
TestDisk is pretty good at repairing a disk well enough to make your data usable again. But its would have to be prefect to repair a windows installation. All  it takes is a few twisted bits in the wrong place to make it impossible to boot windows.  

IF it were mine I'd get the data I want to keep copied off to an external drive. For that [Knoppix Linux]("http://www.knoppix.net/") is what I use. 

The XP CD does have a repair install option where it tries to save you data while reinstalling windows. Try that.

IF that doesn't work your looking at a fresh install of windows.

---

### Post by noskillz on 2008-04-07
Looks like that is what I'll have to do. I already gave in to the fact I would most likely lose all my stuff, so I think when I can scrounge up an XP cd I'll try the repair option you mentioned. Thanks.

---

