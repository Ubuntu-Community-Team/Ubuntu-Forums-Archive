---
title: "Grub error 21"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ryanfx on 2007-07-31
So I tried installing ubuntu and now I am getting a grub error 21.

I defragged my disk, went into the ubuntu installer, selected the first one to resize my partition, and let ubuntu handled the rest.  I currently have HD's in the machine that are mirrored.

I'm a complete linux n00b, so if you have any suggestions, if you could post the link of where I could find more information about it I would really appreciate it, as of now I have no computer! :(

This is the output of my current sudo fdisk -l




```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19451   156240126    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17061   137042451    7  HPFS/NTFS
/dev/sdb2   *       17062       19351    18394425   83  Linux
/dev/sdb3           19352       19457      851445    5  Extended
/dev/sdb5           19352       19457      851413+  82  Linux swap / Solaris


```

---

### Post by nitro_n2o on 2007-07-31
check this out it might help [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by nitro_n2o on 2007-07-31
btw error 21 means that grub can't find the disk where boot files are

---

### Post by MQMike on 2007-07-31
You may need to re-install GRUB.

First, you need to get a grub prompt (grub>). 
Use your Live Kubuntu CD.  Put your Live CD in the CD tray, re-boot your PC, startup your Live Kubuntu.  
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing 
sudo grub  (then press Enter), 
and type the following (press Enter after each command):
grub>  root (hd1,1)          # (hd1, 1) is the partition of your Ubuntu
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.


- - - - -

Edit the boot menu (/boot/grub/menu.lst)?

After doing all this, you may still have to edit the boot menu for GRUB, which is contained in Ubuntu at /boot/grub/menu.lst.  (.lst is an “l” as in “list.”)
You must edit it as root, and don’t forget to save your changes when you are done (File-Save, File-Quit).

The part you need to check/edit is the boot menu for Windows, which should look like:

title Windows XP on or whatever you wish to call it
rootnoverify (hd0, 0)
makeactive
chainloader +1

where:
(hd0, 0) is your Windows partition (hard drive hd0, partition 0)..
(GRUB, the bootloader starts counting from zero.  So hd0 is the first hard drive, hd1 is the second hard drive, etc.;  the first partition is partition 0, the second partition is partition 1, etc.)


For all the details:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
Or,
Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

### Post by ryanfx on 2007-07-31
I'm at this step:

```

grub> find /boot/grub/stage1
 (hd1,1)

grub> root (hd1,1)

grub> 


```


Should the next thing I type be

```

setup (hd0)

```

or


```

setup (hd1)

```

?

I tried hd0, and rebooted and that yielded the same result (error 21).  If this was the right thing to do, let me know and I will try to edit the boot menu!

---

### Post by ryanfx on 2007-07-31
Correct me if I'm wrong.. but I think I have a good idea about what's going on.  Did it somehow get confused with my array and is now treating them as two separate drives?  If so... Did I just REALLY mess things up, and is there any way to reverse this?


```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3a99e270-88bd-41c5-9df4-3ec5cd38d033 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3a99e270-88bd-41c5-9df4-3ec5cd38d033 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by MQMike on 2007-07-31
Sounds like RAID, right?  If so, frankly I've not tried these methods with RAID.  Doesn't mean you can't get them to work, I think I've seen some posts on it.
Ooops . . .

---

### Post by ryanfx on 2007-07-31
[IMG]http://i7.photobucket.com/albums/y266/ryanfx/volumw.png[/IMG]

That's my file viewer.  The 149GB is exactly how it looked before this partitioning.  The other 2 partitions I guess are off of the other HD.

I'm hoping that If I rebuild all of this from the other HD, All of this can be reversed?  If so... any bright ideas to do it safely?  it looks like the partitioning and everything didn't even touch the other one.

---

### Post by MQMike on 2007-07-31
I don’t know what RAID does to a Master Boot Record of Windows.
GRUB will overwrite the MBR where Windows once had its stuff.
Usually, if you want to restore that MBR back to how Windows likes it, you simply run your Windows CD and  do the fix MBR thing (I’ve not done it, but have seen it referenced dozens of times).
Raid, I don’t know.
The only thing Ubuntu and GRUB mess up is the MBR where it was installed, probably (hd0) in your case.  That’s all.

---

