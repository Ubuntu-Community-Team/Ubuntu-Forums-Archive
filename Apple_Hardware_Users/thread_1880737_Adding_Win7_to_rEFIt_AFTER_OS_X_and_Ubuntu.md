---
title: "Adding Win7 to rEFIt AFTER OS X and Ubuntu"
date: 2011-11-14
forum: Apple Hardware Users
---

### Post by Dr. McKay on 2011-11-14
For the moment, I have OS X.6.8 and Ubuntu/Kubuntu (both shells) on my internal iMac HD (320Gb, 28Gb Linux, 2Gb linux swap, rest OS X HFS+). I'm using rEFIt and it's working perfectly.

I would now like to add win7 64-bit to the mix. How do I proceed ?  Do I resize my OS X partition using OS X's Disk utility and then simply install win7 on the free space. Will rEFIt recognize the Win7 partition, in addition to the already present OS X and Linux partitions ?

Or is it just wishful thinking on my part ?  

I'm planning to replace my HD with a 1.5Tb one, but I need to be sure I can  get a triple boot configuration working before I perform the surgery on my Mac...

---

### Post by Hatsune Miku on 2011-11-14
> **Dr. McKay said:**
> For the moment, I have OS X.6.8 and Ubuntu/Kubuntu (both shells) on my internal iMac HD (320Gb, 28Gb Linux, 2Gb linux swap, rest OS X HFS+). I'm using rEFIt and it's working perfectly.

I would now like to add win7 64-bit to the mix. How do I proceed ?  Do I resize my OS X partition using OS X's Disk utility and then simply install win7 on the free space. Will rEFIt recognize the Win7 partition, in addition to the already present OS X and Linux partitions ?

Or is it just wishful thinking on my part ?  

I'm planning to replace my HD with a 1.5Tb one, but I need to be sure I can  get a triple boot configuration working before I perform the surgery on my Mac...

For the resizing part, ALWAYS; ALWAYS; ALWAYS!!!! Use the OS X Disc utility for ANY HSF/+ partitions!!! Also rEFIt should be able to boot windows 7 with any other configuration. rEFIt does a Operating System scan at boot and configures the boot loader automatically.

---

### Post by Dr. McKay on 2011-11-14
So the way to proceed :
resize OS X partition with Disk Utility (I'm gonna give Win7 40Gb, leaves me with around 250Gb for OS X), format as MS-DOS (I can always reformat to NTFS with Win7 installer).
Then restart with Win7 disc in drive, rEFIt should recognize the install disk, install Win7. 

Just want to be sure that Win7 installer isn't gonna mess up my bootloader.

Next question : when dual booting using bootcamp, drivers for apple hardware are installed from the OS X disc. I won't be using bootcamp to install Win7, but can I safely install the drivers afterwards WITHOUT messing with the bootloader (which means, the bootcamp driver installer won't mess up the bootloader when installing the startup disc control panel) ?

---

### Post by Dr. McKay on 2011-11-14
Doesn't work, can't resize the OS X partition :
Disk Utility gives me the following error message :

Partition failed
Partition failed with the error:
Mediakit reports no such partition

Any suggestions ?

---

### Post by Hatsune Miku on 2011-11-15
> **Dr. McKay said:**
> Doesn't work, can't resize the OS X partition :
Disk Utility gives me the following error message :

Partition failed
Partition failed with the error:
Mediakit reports no such partition

Any suggestions ?

Run disk a check

---

### Post by Dr. McKay on 2011-11-16
> **Hatsune Miku said:**
> Run disk a check

With what? Onyx or another tool ?
Any suggestions ?

---

### Post by davidryderuk on 2011-11-18
I originally suggested using diskutil, but have since had problems with the program. I guess Disk Utility is the only way of doing repartitioning on a Mac. Sorry.

You can run a disk check by going to disk utility, selecting the appropriate partition and clicking on verify disk. 

[http://support.apple.com/kb/ht1782](http://support.apple.com/kb/ht1782)

---

### Post by Dr. McKay on 2011-11-18
> **davidryderuk said:**
> I'm just guessing, but I don't think Disk Utility will let you resize the Mac partition whilst a Linux partition is on the same disk. However the diskutil command line program might (also made by Apple).

[http://www.macworld.com/article/55274/2007/02/marchgeekfactor.html](http://www.macworld.com/article/55274/2007/02/marchgeekfactor.html)

You can run a disk check by going to disk utility, selecting the appropriate partition and clicking on verify disk. 

[http://support.apple.com/kb/ht1782](http://support.apple.com/kb/ht1782)

I'll try that, thx !

---

### Post by davidryderuk on 2011-11-23
Deleted,
See my previous post.

---

