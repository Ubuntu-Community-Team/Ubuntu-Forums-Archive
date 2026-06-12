---
title: "Install Xubuntu on Macbook Pro"
date: 2014-06-25
forum: Apple Hardware Users
---

### Post by Mathias_Radtke on 2014-06-25
Hi
today i messed up my gentoo install so hard that i coould not save it anymore.

so now i decided to install Xubuntu on my Macbook Pro 8.2

The tryout worked very fine and i decided to install it
so picked the partition where gentoo is installed, 
made the bootloader install on /dev/sda4, the partition i select ion the apple efi bootloader

then the systems boots to a black screen with only GRUB written in the left corner and a blinking whitespace


what have i done wrong?

the partitioning is the following
dev/sda1 = 100mb free space
dev/sda2 = OSX partition
/dev/sda3 = more free space
/dev/sda4 = Xubuntu install

please help so i can finally use my laptop again

---

### Post by splyntm on 2014-06-28
This is what I do when installing a new Ubuntu distro on my MacBook Pro:

- Boot into OS X

- Remove all partitions other than the main one that OS X uses, which should be called HD by default. To do this, open Disk Utility, click the whole hard drive from the panel on the left (not the underlying partitions). Click the partitions tab. Click on the partition you want to remove and click the minus (-) button. For the Linux Swap partition, you'll have to click that partition on the left panel and erase it to something other than linux swap. Go back to the partition tab of the entire hard drive and remove that partition. Other than the main partition for OS X, everything should be unallocated space. (P.S. You may be worried about Mac's Recovery partition, but that's hidden from Disk Utility)

- Reboot your computer and start installation as you did before, which I assume is via a USB drive or CD using rEFIt or rEFInd (I recommend rEFInd)

- During installation, I usually just pick the option to install alongside Mac OS X instead of dealing with it manually because MacBooks are delicate as far as linux installations go. 

Hopefully this helps.

---

### Post by Mathias_Radtke on 2014-06-28
this helped

i did not need any EFI boot manager when i used gentoo, Xubuntu installed the EFI version and could obivously not be found without these EFI bootloaders

---

### Post by este.el.paz on 2014-06-29
> **Mathias_Radtke said:**
> Hi
so picked the partition where gentoo is installed, 
made the bootloader install on /dev/sda4, the partition i select ion the apple efi bootloader

then the systems boots to a black screen with only GRUB written in the left corner and a blinking whitespace
what have i done wrong?
please help so i can finally use my laptop again

> **splyntm said:**
> This is what I do when installing a new Ubuntu distro on my MacBook Pro:

Other than the main partition for OS X, everything should be unallocated space. (P.S. You may be worried about Mac's Recovery partition, but that's hidden from Disk Utility)
- Reboot your computer and start installation as you did before, which I assume is via a USB drive or CD using rEFIt or rEFInd (I recommend rEFInd)
- During installation, I usually just pick the option to install alongside Mac OS X instead of dealing with it manually because MacBooks are delicate as far as linux installations go. 

Hopefully this helps.

@Mathias:

Where you went wrong?  If you chose "manual" install, which it seems like maybe you did, you then need to at least set up three partitions,  the "home"--flagged as "/" . . . the "swap" . . . and about 10MB in front of the home flagged as "bios_grub" or something like that.  There needs to be a partition "made" for GRUB to call home . . . .  

But, splyntm's suggestion of setting up "free space" or space labeled as "FAT" in OSX DU, and then choosing "Install alongside OSX" is probably the easiest . . . and I used to do that method, but then I think the installs I was doing in LM16 got persnickety going that way and would "lose" the GRUB space, so I went back to the "manual" for my linux installs.  You should try the easy "automatic" way first; and I am using rEFInd on my triple boot MBPro, but apparently the "mac" version might not need the EFI boot manager any more???  

GRUB is about 10MB; Home is however much space you have left after considering the swap; swap it seems like the installer uses the RAM in GB??? rather than the 2x RAM that some places have recommended.  Don't forget to check the md5sum number for the iso . . . it needs to match these days.

e.e.p.

---

