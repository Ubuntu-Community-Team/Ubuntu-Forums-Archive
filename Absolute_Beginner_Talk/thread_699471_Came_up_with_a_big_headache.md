---
title: "Came up with a big headache"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jediscout on 2008-02-17
My windows system crashed after installing some security software. It ended up displaying the grub command in the ethernet boot screen but wouldn't do anything after typing any command at all. Although after I put fiesty back into the cd rom it was able to boot windows one time before the OS failed or disappeared. So now I have a bit of a jumbled mess with several installs of feisty and one that was upgraded to gutsy.
I would like to continue using a dual-boot system, so should I just reload feisty telling it to use entire disk and reformat when installing a windows product at a later time? Any help would be much appreciated.

(Unfortunately I have no way of backing anything up untill I get an external hard drive, which I hope is soon.)

---

### Post by sb12 on 2008-02-17
if you install windows second you will need to reinstall grub, windows overwrites grub with its own bootloader.  you could use a gparted livecd to remove the ubuntu partitions then just reinstall ubuntu though

---

### Post by sailor2001 on 2008-02-17
install windows first, and then install gutsy...; much much easier

---

### Post by jediscout on 2008-02-17
Thanks for the help sb12 and sailor2001, 

I was hoping installing linux first would be better.

I want to completely remove all the OS's first from the hard drive on this old D400 Dell computer. I was going to dedicate 30 gigs to windows and 7 for linux.
I'm still a newbie to this, so what is the step by step approach or the easiest way of doing it? Do I do it from the boot screen or go into the BIOS?

---

### Post by sb12 on 2008-02-17
> **jediscout said:**
> Thanks for the help sb12 and sailor2001, 

I was hoping installing linux first would be better.

I want to completely remove all the OS's first from the hard drive on this old D400 Dell computer. I was going to dedicate 30 gigs to windows and 7 for linux.
I'm still a newbie to this, so what is the step by step approach or the easiest way of doing it? Do I do it from the boot screen or go into the BIOS?

if you want to completely wipe the drive and install linux first, just boot up the install cd and tell it to use all available space on the drive.  You can use a gparted cd to resize later.  If you install windows first, just put in the windows cd and it will clear everything

---

### Post by jan quark on 2008-02-17
here is a nice site covering the dual booting

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by gotee12 on 2008-02-17
IMHO...

I'd simply reinstall Windows first. In the Windows set up, delete the partition tables which will then, in effect leave the entire hard drive unpartitioned. Then have Windows create a 30Gb partition to use as the Windows partition. Finish installing Windows.

Then boot off of your Ubuntu 7.10 Live Cd and have Ubuntu install to the rest of the unpartitioned space on the hard drive. Also keep in mind that you'll want to have a Swap partition. I'd suggest creating a 28Gb Windows install, a 7Gb Ubuntu install and a 2Gb Swap partition.

---

### Post by jediscout on 2008-02-17
Thanks again sb12 and Jan Quark.

---

