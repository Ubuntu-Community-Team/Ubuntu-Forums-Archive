---
title: "Boot Delay on Macbook pro 11,1 (mid-2014) with Ubuntu 16.04"
date: 2016-11-12
forum: Apple Hardware Users
---

### Post by Wellconnected on 2016-11-12
Dear All,
I don't post much since many solutions are to be found, but now I am a stuck on a little annoying behaviour 
that I cannot fix.

I don't think this is an Ubuntu problem, but perhaps there are people here with the knowledge to help me...

I have a Macbook Pro 11,1 with a Retina screen. I have kept OSX installed, but have shrunk it as much as possible.
I have a linux installation on an encrypted LVM with an unencrypted /boot.
The top 200MB partition is VFAT and I have installed the EFI Grub to it and all is fine.
I seem to be able to live with or without rEFIt/rEFInd

When I press the power button I have to wait 30s before I get a rEFInd/EFI screen and after I ask Ubuntu to boot
I have another 30s before I have the window to unlock the disk.

I cannot understand how, but this laptop when to service a few months ago, and came back with both delays
reduced to zero (great!!) but now both have started happening again.

In order to try to "fix" the boot delay, I've reformatted the 200MB /dev/sda1 as HFS+ as per
[https://medium.com/phils-thought-bubble-of-recent-stuff/ubuntu-14-10-running-on-my-macbook-18991a697ae0#.o43wzzplu]("https://medium.com/phils-thought-bubble-of-recent-stuff/ubuntu-14-10-running-on-my-macbook-18991a697ae0#.o43wzzplu")
Also tried a separate HFS+ partition, all to no avail.

I've then gone back to the FAT and installed refind, and done bless, and still 30s!

Also reset the SMC and NVRAM a number of times.

Any help would be greatly appreciated.

---

