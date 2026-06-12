---
title: "Installing Gutsy on a Mac Mini"
date: 2008-02-23
forum: Apple Intel Users
---

### Post by noxocube on 2008-02-23
Right, Imagine Im a total newbie at this (imagination should be made easier because I am)

I have installed Ubuntu a while back on a Windows XP Laptop but Im not sure if it's going to be massively different or not due to the different hardware

I've had a look through the forums and wiki and I can't find a detailed guide to installing on a 1.66ghz Core duo Mac Mini (512mb RAM and a 60gig HD)

I've downloaded the latest Gutsy 64bit iso and I've burnt it to a blank CD using Disk Utility where I need guidance now is in what to do next...

Should I totally replace OSX or should I have keep it and leave myself the option of either OS? I only really use my Mac for Browsing, DVD's & Music as I have an Xbox 360 for my gaming needs.

Any help here is very appreciated some time in advance!!

---

### Post by cyberdork33 on 2008-02-23
I would leave a small OSX partition (or an install on an external device) for firmware updates.

---

### Post by benhall on 2008-02-23
It's quite easy to install linux on the mac mini, but there are a few things you ought to be aware of that are unique to Macs. I've followed these steps when installing linux on mac mini's in the past (I've done this about 6-8 times, on different machines)

1)Resize the partitions using "Boot Camp"; this is in Applications/Utilities on the Mac. As cyberdork33 suggests leave some space for the Mac for firmware updates (for Tiger I think I left between 5 and 10 GB, but Leopard might need more). Make sure that you have all the recent firmware updates installed before trying installing ubuntu.
2)Boot the gutsy cd (hold c when starting up). Do you have a core or core2 duo? I don't think the original intel core processors had 64 bit, but core 2 are. Also, what do you hope to get from using 64 bit gutsy? I don't think its as well supported as 32 bit (hence haven't moved from it), but I could well be wrong, and I don't need dual precision often.
3)You should get the live ubuntu desktop on boot. Double click "install" and configure as you wish. The only default you need to change is to select "use free space" when it gets to the partitioning stage. Finish the install and reboot.
4)To boot into ubuntu, hold down the option key on your keyboard when starting up, and when given a choice of partitions, choose "windows" (a default label). If you don't like this, you can install "rEFIt" on the Mac OS which is more configurable and generally a bit easier to use.

I think that this is everything. The only thing I can't remember is whether you need to specify where to install grub (a linux boot manager), but as I think this installs to the root partition by default you don't need to worry about it. If you get a choice, install to the root partition. Hope this helps

---

### Post by treeves on 2008-02-23
I installed it on my Mac Mini with no problems.  I have Compiz and all drivers working properly.

---

### Post by handy on 2008-02-24
I used the Ubuntu 7.10 64bit Alternate installation, on an iMac Core2Duo, after first installing [***_rEFIt_***]("http://refit.sourceforge.net/") to simplify dual booting with Leopard. It all went really easily.

I know I have a different computer, the reason I'm posting is to recommend the 64bit install if you have a Core2Duo, as the 64bit Ubuntu works really well with 32bit now, as there have been some libraries created to smooth out the old problems.

Good luck!

---

### Post by noxocube on 2008-02-24
Im still using Tiger :P So I dojn't have a copy of bootcamp. Is there anyway I can set the partitions properly using 3rd party software?

---

### Post by cyberdork33 on 2008-02-24
gparted can shrink your OSX partition.

---

### Post by benhall on 2008-02-24
gparted can shrink the OSX partition, but you should be careful- I think that you need to turn off journalling on the partition in OSX before you resize it (I have rendered a partition unbootable by doing this). Search the forums for advice on how to do this properly (sorry i can't offer better advice).

Another alternative would be to use the disk utility you can get access to on installing OSX, which may be more reliable.

To handy: what are the benefits you get from running 64 bit rather than 32 bit? I'm not trying to be awkward, but there have always seemed to be more disadvantages (binary compatibility, drivers etc) than advantages (mostly for scientific calculations and some video editing). It's been a while since I considered 64 bit though, so I might be a bit out of date.

---

### Post by cyberdork33 on 2008-02-24
> **benhall said:**
> Another alternative would be to use the disk utility you can get access to on installing OSX, which may be more reliable.Disk Utility in Tiger cannot shrink your partition, only repartition the entire drive. You can shrink the partition from the commandline though using 'diskutil resizeVolume'. This is the utility that Bootcamp uses to resize the partition.
[http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes](http://www.macgeekery.com/tips/cli/nondestructively_resizing_volumes)

> **benhall said:**
> what are the benefits you get from running 64 bit rather than 32 bit? I'm not trying to be awkward, but there have always seemed to be more disadvantages (binary compatibility, drivers etc) than advantages (mostly for scientific calculations and some video editing). It's been a while since I considered 64 bit though, so I might be a bit out of date.Everything will move to 64 bit eventually anyway. Might as well make the transition now. there are not nearly as many problems with it now as there used to be. Here is a sticky from the 64bit forum that lists advantages / disadvantages:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

