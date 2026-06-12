---
title: "Ubuntu 9.10, Macbook Pro 5,1, OSX 10.6.1 NIGHTMARES"
date: 2009-10-31
forum: Apple Hardware Users
---

### Post by kettle on 2009-10-31
Hi,
(posted this in the wrong area before)
I've recently purchased a brandnew Macbook Pro 5,1 with a 128GB SSD drive, running OSX 10.6.1 and have been struggling all day in vain to install a working version of Ubuntu 9.10. So far I've had no success but have had the questionable pleasure of reinstalling OSX, as well as Ubuntu 10+ times each. 

I've gone through many of the forums and help threads and walkthrus all in vain. In particular I tried both of these walkthrus,

[http://help.ubuntu.com/community/Mac...elInstallation](http://help.ubuntu.com/community/Mac...elInstallation)
and,

[https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

Although I seem to have no problem setting up the partitions, and installing Ubuntu, I have had absolutely no luck getting Ubuntu to subsequently reboot. 

I initially tried doing things exactly according to the tutorial, using bootcamp to create the initial partition, then from the LiveCD erasing the bootcamp partition, going through the Ubuntu setup and finally selecting the grub installer so that it points to sda3. 
Later on I tried pointing the grub install at a variety of different partitions, all to no effect.

It seems that, no matter what I try the end result is that a. I cannot run the sync utility from rEFit, because the grub loader is loader partition is not recognized, causing an 'unknown' filesystem error which rEFit chokes on. This same error causes BootCamp and the OSX partition utilities to choke so that the only way to get back to a reasonable state is to again load the live cd and clean out the ubuntu partitions completely. I also tried removing rEFit after the install, this did not work, also tried booting directly with and without refit via the 'alt/option' key again to no effect. I tried flipping the bios and boot flags on the ubuntu partitions from the gparted interface on the live cd again to no effect. 

My current partition setup is as follows,

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    130170919  Mac OS X HFS+
 3      130170920    130172873  Unknown
 4      130172874    232520530  Basic Data
 5      232520531    236978142  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    130170919  af  Mac OS X HFS+
 3      130170920    130172873  ef  EFI System (FAT)
 4 *    130172874    232520530  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 130170920:
 Boot Code: None
 File System: ext2
 Listed in GPT as partition 3, type Unknown
 Listed in MBR as partition 3, type ef  EFI System (FAT)

Partition at LBA 130172874:
 Boot Code: Unknown, but bootable
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 232520531:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

```

I am kind of at my wits end at this point so any advice, including a recommendation for an older version of Ubuntu that might be more reliable, will be very happily received.

---

### Post by kettle on 2009-10-31
A little more info.  I notice that if I set the partition flag for the grub partition to bios_grub then invariably gptsync chokes and the bootcamp assistant also is unable to function.  If i set the 'boot' flag for the bios partition however, it becomes possible to run gptsync from rEFit - and the result is that hte partitions are already synched.  However if i try to boot ubuntu, either from rEFit or from 'alt/option' then I end up with a screen which just prints,
'GRUB GRUB GRUB GRUB' 

in a loop across the screen.

---

### Post by kettle on 2009-10-31
although im not the least bit certain about this, other comments/posts that seem related all seem to point to GRUB2 as the culprit. This appears to be new to koala so I'm going to try my luck with 9.04 and see if my troubles just evaporate...

---

### Post by Fra_221187 on 2009-10-31
I have a MacBook 2,1 with Mac OS X 10.6.1 installed and I'm trying to install Ubuntu 9.10 too.

If I install it using the "largest contiguous free space" option then when I reboot and try to sync via rEFIt i get the "unknown" filesystem error.

If I manually set the partitions during the install rEFIt tells me that I don't need a sync but when I boot the Linux partition I get a "GRUB hard disk error" screen.

This is my partitions schema:
/dev/sda1 EFI
/dev/sda2 Mac OS X
/dev/sda3 linux (I've tryed both EXT3 and EXT4)
/dev/sda4 linux swap

P.S. I've installed GRUB in /dev/sda3

I've also tryed installing Ubuntu 9.04... same situation!

---

### Post by kettle on 2009-10-31
I've now tried installing 8.04 Intrepid and the results, while slightly better are still rather disappointing.  I installed 8.04 without incident using the largest contiguous open space option, then in the rEFit menu it shows the tux guy but, after clicking the tux icon it goes to a grub screen with a blinking curso and just hangs there indefinitely.  Same deal with 'alt/option' start.  

This has so far been a huge bummer.  I've been running ubuntu and XP on my Panasonic letsnote for the past 2 years and was really hoping to get the best of both worlds out of this new purchase but it looks like this new macbook is simply incompatible with ubuntu at this point.  Unfortunately I need OSX now for development purposes so I guess this means I have to just figure out how to get by without linux.

---

### Post by Fra_221187 on 2009-10-31
I successfully installed Ubuntu (I don't remember what version :S) in dual boot with Leopard on my MacBook so it isn't an hardware issue.

---

### Post by kettle on 2009-10-31
Ok so I tried re-installing 8.04 one more time and this time - FINALLY - success.  I erased all my previous non-OSX related partitions, and then installed from the CD using the 'use largest contiguous open space' option again.  The only difference was that this time I did NOT go to the 'advanced' features section at the end of the Ubuntu configuration/setup.  I just used all default settings.  No rEFit either.  The resolution is kinda lame still but it is actually working so I'm pretty happy. 

I'm going to try upgrading to 9.10 now and see  whether or not all hell breaks loose.

---

### Post by kettle on 2009-10-31
I've now successfully upgraded from 8.04 -> 8.10 .  Now trying 8.10 -> 9.04 .  Fingers crossed!

---

### Post by domedmunds on 2009-10-31
i went through a similar process last week, you can find out more here: [http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229)

at the end of the day removing rEFIt and using the alt key to choose partition to boot from worked.

have a read and let me know if it helps.

d

---

### Post by kettle on 2009-10-31
successfully upgraded from 8.10 -> 9.04 .  Now for the final upgrade: 9.04 -> 9.10 . Fingers crossed one more time.

---

### Post by kettle on 2009-10-31
successfully upgraded from 9.04 -> 9.10 .  finally. thanks to domedmunds as well for providing the additional thread.  my understanding is that the real issue is that grub2 is a mess as far as mac osx 10.6.1 and macbook pro 5,1~ are concerned.

---

### Post by Fra_221187 on 2009-10-31
Ubuntu 9.04 doesn't use GRUB2 but doesn't boot...

---

### Post by eupeso4 on 2009-10-31
Sorry about my poor english, im from Brazil.
I have a 17¨ 5.1 macbook pro.
I have successfully all the  led snow (10.6, ubuntu 9.10 64 and Win 7 64).
Here`s my recipe:
Fisrt off all installed osx 10.6 full on hd, using all the space.
Later, alredy on osx, started bootcamp utility and setted a 100gb 
partition for windows. Do not install rEFIt at this time, or remove it if you alred had it, by deleting /EFI folder on osx and the /Library/startupitems/EFIblesser or something like it, on refit site theres a uninstall guide.)
After that reboot macbook without win cd on drive, but using a partition
distro, called parted magic, but you can use ubuntus live cd and call gparted from there.
Once on gparted, resize win partition (or just format it to ext4 or your
preferred fs in case of not installing windows) and then on the new free space create your linux partition, without formatting the win partition.
Then reboot macbook with win cd and then install win 7 choosing bootcamp partition and formatting it to ntfs and proceed with win install.
After win finish its installation reboot to osx install rEFIt then reboot, if rEFIt do not show, boot to osx then reboot again, this is normal. once rEFIt is loaded on startup enter the sync tool and sync your gpt with mbr. 
Insert Ubuntu cd on drive and boot it, choose install ubuntu.
On the partition setup scheme choose manual partition setup then
just format your Linux partition with your preferred fs and point / to it.
I'd choose to not setup a swap partition duo to 2 facts:

Fisrt: MBR just support 4 primary partition, and in this setup efi consumes 1 partition, osx 1, win 1 and linux the other. If you choose not to install win you can use swap.

SECOND: i have 8gb ram and do not need swap.

On the install progress there will be a ¨advanced¨ button, click on it and choose to install grub on the linux partition, sda3 or sda4, depending on your setup and not on sda (hd0), this is important.

After ubuntu is installed reboot and the rEFIt will show the 3 systems.
If win or ubuntu do not boot on the first try, dont panic, hold power
button to shutdown and then try booting again, all will run ok.

---

### Post by kettle on 2009-11-01
> **Fra_221187 said:**
> Ubuntu 9.04 doesn't use GRUB2 but doesn't boot...
Hmm... that is even worse then.  I don't know what to tell you.  I had to install 8.04, which went ahead without any problems, and even setup the Tux icon all pretty for rEFit, and then ugrade step-by-step all the way to 9.10 .   So basically, I did the following,

> fresh install of snow leopard

> use bootcamp assistant to setup the partitions

> burn CD of Ubuntu 8.04

> install rEFit
   **NOTE: the rEFit bit is optional.  At first I thought rEFit was the problem, but that doesn't seem to be the case.  It should work either way, but the Tux guy is better looking than the hard-drive that gets stuck there by default, and rEFit is nice in that it doesn't require you to be quite so vigilant when starting up the machine.

> boot up from the 8.04 LiveCD

> use gparted to erase the bootcamp assistant bit

> install 8.04 from the LiveCD, leaving all the configuration details including the final 'advanced' portion of GRUB to whatever the default is ( HD0 I think )
      **NOTE: this creates a different partition setup for Ubuntu than 9.04 or 9.10 did for me.  In particular, where 9.04 and 9.10 invariably created a special 'bios' partition, regardless of the settings I tried to specify in the 'advanced' section of the final pre-configuration dialogue, 8.04 setup everything on SDA3.  

> Reboot.

> choose the Tux guy from rEFit and viola!

> use the package manager to upgrade 8.04 -> 8.10

> use the package manager to upgrade 8.10 -> 9.04

> use the package manager to upgrade 9.04 -> 9.10

> configure odds and ends.

I have no problems actually Running Ubuntu 9.10 and the only thing that seems to have really changed is the way the partitions are setup by default so my feeling is that the issue lies there, if not with GRUB2 then with GRUB settings for the last couple of iterations.  In any case, although slow and annoying this seems like a pretty safe way to successfully make the install.

---

### Post by kettle on 2009-11-01
@eupeso4  thanks for the additional info.  hopefully this will all reach a point where it will no longer be an issue!

---

### Post by Nikos.Alexandris on 2009-11-01
> **kettle said:**
> @eupeso4  thanks for the additional info.  hopefully this will all reach a point where it will no longer be an issue!

Just FYI: I recommend to make a clean install and not to upgrade from 9.04. The reason is that if you haven't had a clean install of 9.04 with ext4 being the partition type for /(root), /home, etc., you won't feel the speedy Ubuntu Karmic at all.

I did a clean install yesterday and the system was never that fast. Most of the things work out of the box anyway...

Regards

---

### Post by Fra_221187 on 2009-11-01
I agree with Nikos.Alexandris but at the moment it seems that it's impossible to do a clean install of Ubuntu 9.04 or 9.10 on a MacBook (2,1 and 5,1)

---

### Post by eeshan.mulye4 on 2009-11-06
why did you buy a mac if you wanted to install ubuntu.

---

### Post by Fra_221187 on 2009-11-06
I have a lot of free space on my hdd and I'd like to try Ubuntu, but I don't need it.

---

### Post by linuxopjemac on 2009-11-06
> I agree with Nikos.Alexandris but at the moment it seems that it's impossible to do a clean install of Ubuntu 9.04 or 9.10 on a MacBook (2,1 and 5,1)

I don't agree. I installed Karmic Koala from CD over the old partition wherein 8.10 resided on a MacBook 2,1.

---

### Post by Fra_221187 on 2009-11-06
Do you have reinstalled GRUB?

---

### Post by linuxopjemac on 2009-11-06
I did everything automatically (default), the new version of GRUB was installed automatically on my root partition (/dev/sda3). In the installer I deleted the old ext3 partition and formatted it as ext4 and set it as root. The only thing I experienced was that rEFIt did not see the ext4 partition as Linux but as a Legacy OS.

---

### Post by Fra_221187 on 2009-11-06
I'll try your method as soon as possible. Thank you!

---

### Post by buntuLo on 2009-11-06
i did the same on MBP5,1, karmic over intrepid.
first i reorganised all the partitions with gparted from livecd, and actually changed their order. i installed karmic, but refit would not see grub2 on my ext4 sda4 root partition. i then reverted the order of my partitions, and reinstalled karmic over sda3 (where intrepid was): refit recognised (as legacy os) grub2 on ext4 sda3. the rest went just smooth.

---

### Post by Fra_221187 on 2009-11-06
This is my partitions order:
/dev/sda1 EFI
/dev/sda2 Mac OS X
/dev/sda3 EXT4
/dev/sda4 linux swap

---

### Post by linuxopjemac on 2009-11-06
> This is my partitions order:
/dev/sda1 EFI
/dev/sda2 Mac OS X
/dev/sda3 EXT4
/dev/sda4 linux swap 

I have the same as you

---

### Post by kevpatts on 2009-11-08
> **kettle said:**
> A little more info.  I notice that if I set the partition flag for the grub partition to bios_grub then invariably gptsync chokes and the bootcamp assistant also is unable to function.  If i set the 'boot' flag for the bios partition however, it becomes possible to run gptsync from rEFit - and the result is that hte partitions are already synched.  However if i try to boot ubuntu, either from rEFit or from 'alt/option' then I end up with a screen which just prints,
'GRUB GRUB GRUB GRUB' 

in a loop across the screen.

Kettle, I'm having this problem when I do a standard install. I just get GRUB GRUB GRUB GRUB looping away. How do I change the flags to sort this problem? I'd prefer not to be using rEFIt.

---

### Post by Nikos.Alexandris on 2009-11-08
> **eeshan.mulye4 said:**
> why did you buy a mac if you wanted to install ubuntu.

I have a question for you: why do people climb mountains?

---

### Post by andrewroth on 2009-11-09
I've been triple-booting my macbook pro since 8.04 with refit (mac/linux/winxp).  I haven't upgraded it since 8.04 and bit the bullet for 9.10.

Unfortunately, now I get the grub message and instant reboot.  It's very difficult to debug because there's no help at all, just a hard reboot.  Has anyone been able to solve this yet?

I've tried both grub2 and grub1.  Thinking of trying lilo even.  Any other ideas?

[EDIT] Here's some more info

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          26        3933    31383532   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            3933       19174   122421248   af  HFS / HFS+
Partition 3 does not end on cylinder boundary.
/dev/sda4           19206       24322    41089220    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.

Even though I could not boot in to linux, I used the live CD and the chroot method to get to the install.  A grub-install on the sda2 partition seemed to work.

---

### Post by mercuryknight on 2010-03-15
It seems that formatting partitions using the ubuntu live cd can cause some partition table changes, which lead to the problem that you cannot boot ubuntu. This is because the partition map on intel-mac is unique and only the partition tool provided by Mac OS can work with it well.
 
So I usually use some third party plug-ins with which I can format the EXT partition  under the partition tool of Leopard. Then, when I run the live cd, I choose to install directly into this EXT partition without formating.

---

