---
title: "Is dual booting ubuntu and fedora/openSUSE just as easy as popping in a liveCD?"
date: 2011-11-22
forum: Any Other OS
---

### Post by moorhead98 on 2011-11-22
I wish to dual boot ubuntu (currently installed) with fedora and/or openSUSE. Is it just as easy as popping in the liveCD for each distro and letting the installer work? And if it isn't, could you give instructions on how to get it to work?

---

### Post by jjex22 on 2011-11-22
In theory it is - the installers of fedora and open suse will give you options like - shrink windows, install me/shrink ubuntu install me/ add me to free space.

However if you are going to install three linux, I usually find it's best to first prepare your drive with a [gparted live cd]("http://gparted.sourceforge.net/livecd.php") so you can get the most efficient set up - as well as already having a slot to put the new os into , to reduce the risk of errors.

first things first is back up the hdd - if possible make a clone of the drive to a back up drive.

Then decide how you want the drive set out - I'd recommend putting both your new OS's inside the extended partition - this way you only use one primary 'slot' on your drive -whether you shrink windows and increase the extended partition to the left, or shrink ubuntu, or both.

You don't need to set up any additional swap partitions as both new distro's will automatically select the swap partition.

As a rough guide a basic size for fedora is 10GB, Open SUSE would be about 14GB - but the bigger you can go the better - these aren't minimums, you can go lower, but it makes you less likely to run out of space.

If you have a separate  /home partition you can also set this as your home partition for the new distros, but don't use the same user name as this may overwrite the files - I find it easier to create symbolic links from the /hom directories to their counterparts.

As for the installs, choose manual configuration options for both, and install to one of the partitions you created earlier. They will auto swapon.(Open SUSE supports installing to BTRFS filesystems, but if dual booting, I recommend sticking with EXT4 for now as it makes it easier to run things like fsck from a different partition if you get errors - if sharing a /home partition, changing the filesystem will erase everything on the partition. -just to summerise best to format your desired partition as EXT4 and set mount point as '/' (if you want a shared /home partition, again format to EXT4, set mount point /home.

A couple of things to concider - you can try running them in virtualbox for a bit to see how you like them, or experiment from the live CD's before you install - though for Open SUSE, you'd have to choose gnome or KDE for a live disk - the full disk contains KDE Gnome LXDE and XFCE, but it isn't live - I'd recommend trying KDE as Fedora is Gnome, and Unity is based on Gnome.

I'd also recommend installing Fedora first - 16's been out a bit longer, more fixes, and in general is a less buggy release - Open SUSE has been out a week and at the moment the support for 12.1 hasn't caught up with the release. It's definitely a great KDE experience as always - my personal favourite, but the general release feels more like an RC than a final - after the install the only repo I had activated was the install CD - Genius!

---

### Post by moorhead98 on 2011-11-22
> **jjex22 said:**
> In theory it is - the installers of fedora and open suse will give you options like - shrink windows, install me/shrink ubuntu install me/ add me to free space.

However if you are going to install three linux, I usually find it's best to first prepare your drive with a [gparted live cd]("http://gparted.sourceforge.net/livecd.php") so you can get the most efficient set up - as well as already having a slot to put the new os into , to reduce the risk of errors.

first things first is back up the hdd - if possible make a clone of the drive to a back up drive.

Then decide how you want the drive set out - I'd recommend putting both your new OS's inside the extended partition - this way you only use one primary 'slot' on your drive -whether you shrink windows and increase the extended partition to the left, or shrink ubuntu, or both.

You don't need to set up any additional swap partitions as both new distro's will automatically select the swap partition.

As a rough guide a basic size for fedora is 10GB, Open SUSE would be about 14GB - but the bigger you can go the better - these aren't minimums, you can go lower, but it makes you less likely to run out of space.

If you have a separate  /home partition you can also set this as your home partition for the new distros, but don't use the same user name as this may overwrite the files - I find it easier to create symbolic links from the /hom directories to their counterparts.

As for the installs, choose manual configuration options for both, and install to one of the partitions you created earlier. They will auto swapon.(Open SUSE supports installing to BTRFS filesystems, but if dual booting, I recommend sticking with EXT4 for now as it makes it easier to run things like fsck from a different partition if you get errors - if sharing a /home partition, changing the filesystem will erase everything on the partition. -just to summerise best to format your desired partition as EXT4 and set mount point as '/' (if you want a shared /home partition, again format to EXT4, set mount point /home.

A couple of things to concider - you can try running them in virtualbox for a bit to see how you like them, or experiment from the live CD's before you install - though for Open SUSE, you'd have to choose gnome or KDE for a live disk - the full disk contains KDE Gnome LXDE and XFCE, but it isn't live - I'd recommend trying KDE as Fedora is Gnome, and Unity is based on Gnome.

I'd also recommend installing Fedora first - 16's been out a bit longer, more fixes, and in general is a less buggy release - Open SUSE has been out a week and at the moment the support for 12.1 hasn't caught up with the release. It's definitely a great KDE experience as always - my personal favourite, but the general release feels more like an RC than a final - after the install the only repo I had activated was the install CD - Genius!

So lets say I just wanted opensuse. Would I just pop it in and it would handle the partitioning and /home folders and everything?

---

### Post by jjex22 on 2011-11-22
it does auto create space - but I can't remember if by default it'll take it from Ubuntu or Windows - it will tell you in plain text in a summery screen of what it's about to do. Open SUSE is also nice n that it gives you a final summery screen to check what you're about to do before you commit it to disk. 

By default, Open SUSE will create a ~200MB EXT4 /boot partition, and a / partition formatted in BTRFS - with subvolumes for /var, /tmp/ /usr etc. I think it also creates an EXT4 /home partition, but I can't remember for certain. I do still maintain that it's best to manually configure, but it is of course easier to just use the auto settings.

Either way - make sure you back up the drive first. :)

---

### Post by bsniadajewski on 2011-11-23
If you do install either Fedora or OpenSuse, tell the installer t oplace the GRUB into the root partition of the new install.  That way, you can go back into Ubuntu, fire up a terminal, and enter "sudo update-grub".  It should pick up your new Fedora/OpenSuse installation.

---

### Post by moorhead98 on 2011-11-26
Ok, new idea --- What if I wanted to install arch or linux mint? how would i accomplish that?

---

### Post by satanselbow on 2011-11-26
> **moorhead98 said:**
> Ok, new idea --- What if I wanted to install arch or linux mint? how would i accomplish that?

Same rules apply...

In any dual/tri boot situation you need to decide which OS/Distro is "boss" - ie controls grub(2). You can then as stated above update grub to pick up your additional distros.

You can either install each individual installs grub to it's /root partition (or /boot if that distro insists on having that separation - such as Fedora / Arch).

I have recently taken (where possible) skipping the installation of grub on addition distros altogether and manually building the config by hand.

I would also do all your partitioning in advance in gparted as you have much more flexibility and are less likely to wipe out all that is precious on your existing setup ;)

Unless you are desparate to get really good at partitioning real quick I would suggest running test distros in a VM first so there are less surprises when you come to do it on your real machine ;)

---

### Post by moorhead98 on 2011-11-26
> **satanselbow said:**
> Same rules apply...

In any dual/tri boot situation you need to decide which OS/Distro is "boss" - ie controls grub(2). You can then as stated above update grub to pick up your additional distros.

You can either install each individual installs grub to it's /root partition (or /boot if that distro insists on having that separation - such as Fedora / Arch).

I have recently taken (where possible) skipping the installation of grub on addition distros altogether and manually building the config by hand.

I would also do all your partitioning in advance in gparted as you have much more flexibility and are less likely to wipe out all that is precious on your existing setup ;)

Unless you are desparate to get really good at partitioning real quick I would suggest running test distros in a VM first so there are less surprises when you come to do it on your real machine ;)

So if I want Ubuntu as the boss distro, then I would just download an iso for something like mint, then put it in the /root partition, then update grub? 

Sorry if I sound like a no0b, I'm new at multi distro booting

---

### Post by jjex22 on 2011-11-26
Hello again,

Yes in the case of mint, where it will by default just create a / partition, then you install the bootloader to the same partition as you've marked mount at /, for example

/dev/sda4

instead of 

/dev/sda

In the case of mint it isn't the end of the world if you forget to move the bootloader, it'll just overwrite ubuntu's and shouldn't have any problem booting - putting the bootloader on the partition of the os is good because it means it isn't over written - limiting problems. 

Whichever bootloader you install last may well get the boot flag - meaning that's the bootloader you'll be sent to - if you want Ubuntu's back in charge, then login to ubuntu and sudo update-grub :)

Personally, I'm with Satanselbow, I manually configure grub.cfg,and don't install a bootloader where possible - though that option seems, irritatingly, to be going out of fashion,  but I've been doing this from the days of grub 0.97 when such things were expected. Whilst this will help a lot with learning about multibooting it can also be a pain and needs more maintenance than letting each distro have a bootloader. I suppose the only advantage is that when booting you only have to go through one bootloader, not a daisy chain where one hands off to another. (I also edit the titles, but I'm fussy like that.

---

### Post by moorhead98 on 2011-11-26
> **jjex22 said:**
> Hello again,

Yes in the case of mint, where it will by default just create a / partition, then you install the bootloader to the same partition as you've marked mount at /, for example

/dev/sda4

instead of 

/dev/sda

In the case of mint it isn't the end of the world if you forget to move the bootloader, it'll just overwrite ubuntu's and shouldn't have any problem booting - putting the bootloader on the partition of the os is good because it means it isn't over written - limiting problems. 

Whichever bootloader you install last may well get the boot flag - meaning that's the bootloader you'll be sent to - if you want Ubuntu's back in charge, then login to ubuntu and sudo update-grub :)

Personally, I'm with Satanselbow, I manually configure grub.cfg,and don't install a bootloader where possible - though that option seems, irritatingly, to be going out of fashion,  but I've been doing this from the days of grub 0.97 when such things were expected. Whilst this will help a lot with learning about multibooting it can also be a pain and needs more maintenance than letting each distro have a bootloader. I suppose the only advantage is that when booting you only have to go through one bootloader, not a daisy chain where one hands off to another. (I also edit the titles, but I'm fussy like that.

So allow me to get this straight (sorry for seeming childish or unsure, just don't want to mess this up)

If I choose a distro like mint that has grub 2 and does not make a /boot partition, All I have to do is run the liveCD, choose it to partition the hard drive so the OS has enough space, boot back to ubuntu by selecting it at grub (or burg, which I may install), then run sudo update-grub so it chooses ubuntu as default?

Please correct me if I am mistaken, and if there is an easier way to do the task without editing grub.cfg, that would be appreciated (Reason why I don't want to edit it is because I don't trust myself - ive messed up package management before by editing sources.list and other things multiple times)

Thanks for the help

---

### Post by inobe on 2011-11-26
for opensuse, if you have a single partition and that partition has ubuntu, it's best to resize the partition with gparted, of course i would do the resize from a live cd.

so now that you resized the hard drive and now you have two partitions, when you install suse, point it to install on that empty partition.

once you reach the user settings, choose not to install bootloader.

on restart log onto ubuntu and do

```
sudo update-grub
```

now restart, and suse will be in ubuntu grub menu, start suse to complete installation.

---

### Post by moorhead98 on 2011-11-26
> **inobe said:**
> for opensuse, if you have a single partition and that partition has ubuntu, it's best to resize the partition with gparted, of course i would do the resize from a live cd.

so now that you resized the hard drive and now you have two partitions, when you install suse, point it to install on that empty partition.

once you reach the user settings, choose not to install bootloader.

on restart log onto ubuntu and do

```
sudo update-grub
```now restart, and suse will be in ubuntu grub menu, start suse to complete installation.

Ok, now say I want to remove of it. Is that at all possible? (just trying to walk through all possible situations, I can't afford messing up my laptop)

And what If I wanted something like chakra or linux mint? how would I go by installing (or removing) that?

---

### Post by inobe on 2011-11-26
formatting the partition will rid of that os on it.

you will just need to update grub from terminal to rid of the useless boot line.


a distro like chakra i believe is similar in a way when choosing not to install a bootloader.

this is all assuming you wish to keep ubuntu and it's boot menu.

---

### Post by jjex22 on 2011-11-26
If you are planning to try out several different distro's then it is best to put their individual boot loaders on their own partition- this way when you remove them, as inobe says, sudo update-grub will do the trick. 

By default, Ubuntu has put it's bootloader on /dev/sda (the MBR). As linux Mint is virtually identical to Ubuntu, the install process will be the same - by default it will free up space, and place it's bootloader on /dev/sda, configure itself, Ubuntu (as it will detect it) and your windows install. This is bar far the easiest way of doing things and the safest - the only thing that will change in your boot process is that your grub screen won't be purple anymore, and linux mint will be the default option. BUT IT WILL ALL WORK. Remember at the end of the day it's the same program - Grub 1.99, just configured from a different OS and with a different graphic.

I maintain that my recommendation regardless of bootloader is to free up the space manually with gparted and install into the free space - whilst not easier than just telling the installer to carve up what it wants, it does lead to better disk management. If you do go for the auto carve route, supposing that your hdd was split in half by ubuntu, it'll be best to take space from ubuntu as it needs around 10GB to fill out whereas windows 7 takes 17GB just at install, and realistically needs more like 40GB

Of course you need to make sure you have backed up your hard drive - the golden rule is no back up, no playing - at the end of the day it's entirely possible using the easy tick boxes to tell a new install to write over the whole disk. So please make sure you back everything up.

I'd also recommend trying to install inside a VM first - download virtualbox, and use this to install linux mint, or use your ubuntu live cd - don't let it auto install, just make a virtual hdd, this way you can do a dummy run of manual partitioning with no risk, you'll also get a better understanding of how it all works, and can just ask us questions as you go - the first time i did it I was using a text based partitioner and had no idea what it was babbling on about!, fortunately times have changed - it's almost friendly!

---

### Post by inobe on 2011-11-26
opensuse, i have never dual booted with windows, however it doesn't auto detect another linux distribution and resize the partition it's on, it only offers to use the entire disk.

now there is an advanced partitioning tool i wouldn't recommend using unless the individual knows how to use it.


is why creating that partition is better and easier, at least if someone wants to give suse a go.

just to clear that up.

---

### Post by jjex22 on 2011-11-26
Sorry inobe, I took it that the op was now looking to try mint or arch instead - as arch is very complicated, I chose to recommend mint's install as an intro to get used to manual installation.

Whilst I run openSUSE atm, I figured if mint is on the cards, again it's a lot simpler - no btrfs; seperate /boot and /home partitions by default, etc. plus it most likely will try and shrink the windows partition by default - that's what it did on mine. I just figured the OP is feeling a bit out of depth, so chose the distro mentioned with the easiest installer first to ease them in :)

---

### Post by inobe on 2011-11-26
no problem jjex22, you've provided good sound advice:D

---

### Post by sophia911 on 2011-11-27
Great Job . 
I will try to test them . 
Dual booting ubuntu is easy as popping in .

---

### Post by moorhead98 on 2011-11-27
> **jjex22 said:**
> Sorry inobe, I took it that the op was now looking to try mint or arch instead - as arch is very complicated, I chose to recommend mint's install as an intro to get used to manual installation.

Whilst I run openSUSE atm, I figured if mint is on the cards, again it's a lot simpler - no btrfs; seperate /boot and /home partitions by default, etc. plus it most likely will try and shrink the windows partition by default - that's what it did on mine. I just figured the OP is feeling a bit out of depth, so chose the distro mentioned with the easiest installer first to ease them in :)

Ok, so any ubuntu based distro that installs on a different partition, can see the ubuntu partition (no windows partition on this), and will put it's bootloader on/dev/sda will be the best option? And how would I set up so ubuntu is default? just update grub? And how would I install it so that the os is on another partition but puts the bootloader on dev/sda (so I can remove it by deleting the partition and updating grub)?

---

### Post by jjex22 on 2011-11-28
Moorhead 98

As for any ubuntu based distro auto configuring for ubuntu - I can't attest for that; some times Ubuntu doesn't set up grub properly for other versions of Ubuntu! but the basic premise is this

back up your disk

Create space on your disk to put the new distro in - ideally within an extended partition.

run the installer - setting up the new partition, and setting the mount point(s) required

Installing the bootloader to the place where you want it - ideally the same partition you've installed your distro to if you plan to remove it.

restart and configure grub - as you won't have installed to the mbr Ubuntu will start as normal, then you run sudo update-grub to hopefully detect your new distro.

If you wanted to install something complicated like arch or gentoo in the future, it really is essential to get the hang of partitioning. If you could give me an idea of the distro(s) you wished to try, I'd be happy to make you a step by step guide to install it alongside Ubuntu to ease you in? To get an idea of what distro's you'd like to put on your machine, I recommend downloading a few live CD's and burning them to disk or usb stick, this'll give you an idea of how they run on your hard ware. Check out [distrowatch]("http://distrowatch.com/") to get some ideas of distro's you're interested in :)

---

### Post by [RMC]Pip on 2011-11-29
Hi,

I would be very greatful if someone could help me in my problem.

I have a Win7 install on my main HD. On another one I would like to try Ubuntu and openSUSE on 2 different partitions + 1 for storage.
Installed openSUSE first then Ubuntu 11.10. I thought ubuntu's bootloader will great me after restart but the openSUSE's one loaded without any option to start ubuntu.

Tried to modify the boot/grub/menu.lst without success (I'm totally new to multiboot stuff) - added this new lines:
> ###Don't change this comment - YaST2 identifier: Original name: Linux other###
title Ubuntu 11.10 Oneiric Ocelot
    rootnoverify (hd0,2)
    chainloader +1
    kernel /vmlinuz root=/dev/sdb3 ro quiet splash
    initrd /initrd.imgThe error I receive:
> Error 13: Invalid or unsupported executable format I thought it's ok, same disk, +1 for the partition number.

Info about my disks:
> Disk /dev/sda: 750.2 GB
Disk identifier: 0xd47ad47a

Device     Boot      Start         End      Blocks   Id  System
/dev/sda1      *              2048  1048578047   524288000    7  HPFS/NTFS/exFAT
/dev/sda2                   1048578048  1465145343   208283648    7  HPFS/NTFS/exFAT> Disk /dev/sdb: 320.1 GB
Disk identifier: 0x7c1041e9

   Device     Boot      Start         End      Blocks   Id  System
/dev/sdb12048     7813119     3905536   82  Linux swap / Solaris
/dev/sdb2      *                  7813120   242188287   117187584   83  Linux
/dev/sdb3        242188288   476563455   117187584   83  Linux
/dev/sdb4              476565502   625141759    74288129    5  Extended
/dev/sdb5        476565504   625141759    74288128    b  W95 FAT32OpenSUSE lines:> title openSUSE 12.1
    root (hd0,1)
    kernel /boot/vmlinuz-3.1.0-1.2-desktop root=/dev/disk/by-id/ata-SAMSUNG_HD321KJ_S0MQJ1PP504532-part2 resume=/dev/disk/by-id/ata-SAMSUNG_HD321KJ_S0MQJ1PP504532-part1 splash=silent quiet showopts vga=0x345
    initrd /boot/initrd-3.1.0-1.2-desktopThis load the MS OS:> title Linux other
    rootnoverify (hd1,0)
    chainloader +1

Thank you for your time!

---

### Post by jjex22 on 2011-11-29
From what I know the problem is that Open SUSE 12.1 is still using grub legacy, and legacy is failing to hand over to the grub 2 of Ubuntu -the chainloader +1 command.

try to boot straight to Ubuntu using this setting

root (hd0,2)
kernel /boot/grub/core.img
boot

With a bit of luck you'll get into Ubuntu, then open a terminal and run 

sudo update-grub

With a bit of luck it will make Ubuntu's gnome 2 the default bootloader and automatically set up OpenSUSE... Fingers crossed!

---

