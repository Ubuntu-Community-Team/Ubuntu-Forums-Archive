---
title: "grub error, how to boot back into mac os x?"
date: 2011-05-06
forum: Apple Hardware Users
---

### Post by unagimiyagi on 2011-05-06
Hi guys,

I am persuaded now (too late) that I need to invest in a robust backup scheme.  

I had refit dual-booting snow leopard and ubuntu 10.10.  

I tried to upgrade to 11.04 and it got stuck on bootup after the upgrade.

So I went into disk utility and deleted what I thought were all partitions except the mac one.  I rebooted, and now I get the grub no partition error.

Did I delete my mac partition? I don't think that I did.  How do I boot back into mac os x?
Using the option key on bootup no longer shows a mac disk and inserting the mac os x system cd doesn't show any options either.

How can I fix this?

Thanks!

---

### Post by srs5694 on 2011-05-06
You may have deleted the EFI System Partition, which is a critical part of booting a Mac. Please do this:


[list=1]
[*]Download and burn [PartedMagic.](http://partedmagic.com)
[*]Boot PartedMagic.
[*]Open a Terminal Window.
[*]Type "fdisk -lu /dev/sda"
[*]Type "gdisk -l /dev/sda"
[*]Post the results of the fdisk and gdisk commands here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings.
[/list]


The fdisk and gdisk output will tell me precisely how your disk is currently partitioned, in terms of both MBR and GPT data structures. That information is critical for deciding how to proceed.

---

### Post by Hatsune Miku on 2011-05-07
> **srs5694 said:**
> You may have deleted the EFI System Partition, which is a critical part of booting a Mac. Please do this:


[list=1]
[*]Download and burn [PartedMagic.](http://partedmagic.com)
[*]Boot PartedMagic.
[*]Open a Terminal Window.
[*]Type "fdisk -lu /dev/sda"
[*]Type "gdisk -l /dev/sda"
[*]Post the results of the fdisk and gdisk commands here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings.
[/list]


The fdisk and gdisk output will tell me precisely how your disk is currently partitioned, in terms of both MBR and GPT data structures. That information is critical for deciding how to proceed.

I keep seeing this and its not true; MACS DO NOT USE THE EFI PARTITION!

Just hold down X during boot up and it will force the Firmware to look for a HFS+ partition and boot from it.

---

### Post by srs5694 on 2011-05-07
> **Hatsune Miku said:**
> I keep seeing this and its not true; MACS DO NOT USE THE EFI PARTITION!

No need to jump down my throat. I just ran a test, and you're right; my 1st-generation Mac Mini booted fine without an ESP.

That said, if the system isn't bootable, running the procedure I outlined *will* produce useful diagnostic information on what partition(s) exist on the disk.

---

### Post by Hatsune Miku on 2011-05-07
> **srs5694 said:**
> No need to jump down my throat. I just ran a test, and you're right; my 1st-generation Mac Mini booted fine without an ESP.

That said, if the system isn't bootable, running the procedure I outlined *will* produce useful diagnostic information on what partition(s) exist on the disk.

Wasnt trying to; it just drives me nuts people keep thinking this. 

```
diskutil list
```

imo is better then everything else to do

Also if he used disk utility in no way he could of deleted in EFI partition.

---

### Post by unagimiyagi on 2011-05-07
> **srs5694 said:**
> You may have deleted the EFI System Partition, which is a critical part of booting a Mac. Please do this:


[LIST=1]
[*]Download and burn [PartedMagic.]("http://partedmagic.com")
[*]Boot PartedMagic.
[*]Open a Terminal Window.
[*]Type "fdisk -lu /dev/sda"
[*]Type "gdisk -l /dev/sda"
[*]Post the results of the fdisk and gdisk commands here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings.
[/LIST]


The fdisk and gdisk output will tell me precisely how your disk is currently partitioned, in terms of both MBR and GPT data structures. That information is critical for deciding how to proceed.

Hi,


Thanks alot for your help.  I tried diskwarrior, and here is some output.
```

This disk is not a Macintosh disk.
This disk is 465 gb in size
disk id: disk0s1
Sectors:976,773,167
Drive Format: FDisk Partition Scheme
File System: msdos

```Diskwarrior can't fix my drive, I'm assuming b/c my hard drive is now a non-mac drive?

I'll show the output from the other commands next that you suggested.

I am thinking that I have actually formatted my disk using disk utility.  I had what I thought were extra partitions (dual booted mac and ubuntu 10 successfully previously).  I wanted to leave just the mac and ubuntu partitions, but I must have formatted the mac partition.  

Mounting my drive in windows 7 (on another laptop) shows only one partition, if that helps.

Thanks a million in advance.

---

### Post by unagimiyagi on 2011-05-07
OK, I am typing from a diff computer.  I've tried to hold down "x" while booting my macbook pro, and that doesn't work.  I booted from the Ubuntu CD and had to hit F6 at the menu and run with a "nomodeset" option in order to "try ubuntu without installing" option to work.  I opened the terminal and typed in "sudo fdisk -lu /dev/sda1"

and got this:

```


Disk /dev/sda1:  500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000000000000

Device Boot    Start   End    Blocks    Id   System

```


Am I correct in that I did not in fact just mess up the partition table; rather, I deleted or reformatted my mac in disk utility on the mac, and I just need to try to recover my files?  I tried testdisk but I'm getting a Read-only error permission denied (despite using sudo) and photorec, but these tools seem to find some files, but they look weird.  Like I set it to find just microsoft office documents but the names make no sense, and it is saying that it will take 24 hours (so I only let it run for 15 minutes to get a flavor for what I can expect to get back).

Any advice would be very appreciated.

Thanks!

---

### Post by srs5694 on 2011-05-07
> **Hatsune Miku said:**
> ```
diskutil list
```imo is better then everything else to do

Also if he used disk utility in no way he could of deleted in EFI partition.

Apple's diskutil command provides limited information, particularly in the case of disks with [hybrid MBRs,](http://www.rodsbooks.com/gdisk/hybrid.html) which contain both GPT and MBR data. The combination of fdisk and gdisk will show both sets of data, if both are present and undamaged. Also, from my own personal perspective, I'm much more familiar with fdisk and gdisk (I wrote the latter!) than I am with diskutil, so I personally am much more likely to be able to properly interpret their output.

[quote=unagimiyagi]Thanks alot for your help.  I tried diskwarrior, and here is some output.[/quote]

I'm not familiar with diskwarrior, so I don't know if it might have quirks that might be relevant to this diagnosis; however, it appears as if something (presumably either the Ubuntu installer or diskutil) has deleted or damaged the GPT data. If the GPT data have been damaged but not entirely deleted, there's a slim chance that you'll be able to recover the data using gdisk. [This page](http://nessus.rodsbooks.com/gdisk/repairing.html) provides some pointers along those lines; however, that page is intended for experts. If you don't understand the issues, I strongly recommend you post back the fdisk and gdisk output and wait for my response. One further tip: If gdisk tells you that it's found both MBR and GPT data, tell it to display the GPT data, and post that back here. (fdisk shows the MBR data, so there's no point in showing it via gdisk as well.)

---

### Post by srs5694 on 2011-05-07
Your latest post arrived as I was typing my last post, unagimiyagi. You typed the wrong command and omitted the second (equally or more critical) command. To reiterate, you need to type two commands:

```

fdisk -lu /dev/sda
gdisk -l /dev/sda

```

My instructions specified doing this from PartedMagic, which includes both tools. If you do it from the Ubuntu installer, you'll need to use "sudo" for both, and you'll need to install gdisk by typing "sudo apt-get install gdisk". Note that the device filename is /dev/sda; you typed /dev/sda1, which is incorrect and produces useless output.

Without seeing the output from both fdisk and gdisk, and perhaps having you run some additional commands using gdisk, I can't say precisely what happened or how difficult it will be to get your data back. I strongly urge you to do nothing potentially destructive, though; messing around with TestDisk or other utilities that write data to the disk could make things much worse than they are now!

---

### Post by unagimiyagi on 2011-05-07
> **srs5694 said:**
> Your latest post arrived as I was typing my last post, unagimiyagi. You typed the wrong command and omitted the second (equally or more critical) command. To reiterate, you need to type two commands:

```

fdisk -lu /dev/sda
gdisk -l /dev/sda

```My instructions specified doing this from PartedMagic, which includes both tools. If you do it from the Ubuntu installer, you'll need to use "sudo" for both, and you'll need to install gdisk by typing "sudo apt-get install gdisk". Note that the device filename is /dev/sda; you typed /dev/sda1, which is incorrect and produces useless output.

Without seeing the output from both fdisk and gdisk, and perhaps having you run some additional commands using gdisk, I can't say precisely what happened or how difficult it will be to get your data back. I strongly urge you to do nothing potentially destructive, though; messing around with TestDisk or other utilities that write data to the disk could make things much worse than they are now!

Thanks alot.  But unfortunately, Parted Magic does not work on my mac.  I burned the iso and stuck it in, and it gets stuck always after I try to run the default settings.  It says "Setting up system devices" and that's it.  I've tried all of the other options, to no avail.  Any ideas about what to do when the rescue tools themselves don't seem to be working?

---

### Post by srs5694 on 2011-05-08
Since you got fdisk working from an Ubuntu install CD, use that. (You'll need to install gdisk, as described earlier.) If that doesn't work for some reason, try [System Rescue CD,](http://www.sysresccd.org) which has both fdisk and gdisk.

---

