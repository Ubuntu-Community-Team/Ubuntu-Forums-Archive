---
title: "Grub boot floppy on zip disk"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Jimbo2184 on 2007-04-18
Hi guys.

I've run into a little bit of a problem with my desktop machine at home after trying to install Ubuntu 6.10 (edgy) from the CD. It installed just fine, but GRUB gives me error 17 and then seems to just hang.

I'm dual booting Windows XP (as the family "need" it apparently and I'm not one for changing their precious OS!) and Ubuntu using the GRUB boot loader.

I hear its possible to boot GRUB using a boot floppy disk, but is it also possible to boot up GRUB using a Zip disk? I removed the old damaged floppy drive from the PC and replaced it with a ZIP 100 drive on the IDE interface.

BIOS recognises the ZIP disk as IOMEGA ZIP 100 in its CMOS settings and offers it as a core boot device, so I was hoping it would be possible to transfer the Ubuntu kernel from the desktop's partition  onto a ZIP disk and boot ubuntu this way?

If its possible it would save having to reconfigure the system BIOS all the time, so when I want to use Linux at home all I need is the boot ZIP disk, and when I'm done, all I need then do is simply umount the ZIP disk and reboot so Windows will then reboot.

Any advice you can offer is greatly appreciated. At least this means I can still use the operating system I love at home as well as on my laptop.

---

### Post by freebird54 on 2007-04-18
I guess it should be theoretically possible - but I don't think you need to do it that way.  Something minor went wrong with your configuration of dual boot, and that can be fixed fairly easily once we know what you've got there.  When done, we can have it defaulting to booting Windows, or even not showing the grub menu on its way into Win, while still allowing you to boot Edgy.

First off, we need to see the result of this command from the Live CD terminal
```

sudo fdisk -l
```

which will give you output similar to:

```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   b  W95 FAT32
/dev/hda2            4869        5129     2096482+  82  Linux swap / Solaris
/dev/hda3            5130       19457   115089660   83  Linux
/dev/hda4            3825        4868     8385930   83  Linux

Partition table entries are not in disk order
```


When we know that, we'll know what do do next to set it up.  This link might help too:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Let us know!

---

### Post by Jimbo2184 on 2007-04-18
Cheers for the input.

I'm afraid I'm not at the PC until the weekend to show you the exact output of fdisk, but what I can tell you from memory is the disk is set up like this:

/dev/hda1 = Windows XP Pro (SP2)   Cap. = 90GB, 50GB Free
/dev/hda2 = DVD Films Cap. 50GB, 0GB Free
/dev/hda3 = Ubuntu Linux (ReiserFS) 34GB approx 30GB Free
/dev/hda4 = Solaris/Linux Swap (1GB)

The total size of the disk is 200GB however BIOS only recognises the first 137GB of any partition (damn IDE block addressing schemes lol) - could that affect GRUB's boot loader?

I initially thought that the CMOS virus protection might cause a problem so I killed that pile of crap as soon as I could, then ran:

root (hd0,3)
setup (hd0)

This was successful but on reboot it still hung with error 17, which I seem to have discovered is an unmountable boot volume...

I hope that helps. I'll be back to sort out the home machine at the weekend, till then I hope that info helps.
I have to admit this one is stumping me!

---

### Post by freebird54 on 2007-04-18
From the look of that, it could very well be a problem.  Is there any chance  of flashing your BIOS to something more up to date?  I had to do that on my c2000 box - to bring it to 2004 status.  However, I saw one possibility.

The steps you took should have worked.  Of course - it should have read
```

*grub> * root (hd0,2)
*grub>*  setup (hd0)
```

if your partition list is correct :)  Grub counts from 0,0 so a,3==0,2

I hope that's all it is...

---

