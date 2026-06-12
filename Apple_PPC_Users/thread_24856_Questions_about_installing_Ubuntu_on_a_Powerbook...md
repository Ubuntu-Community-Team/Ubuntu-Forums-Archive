---
title: "Questions about installing Ubuntu on a Powerbook..."
date: 2005-04-08
forum: Apple PPC Users
---

### Post by Readis on 2005-04-08
I have a few questions about installing Ubuntu on my 17" Powerbook, and  I am hoping people will be willing to answerthem here.  So... here we go...

1. Will I be able to see my OSX partition, and will I be able to write to it?

2. Is there a free program out there that will let me repartition my drive with out needing to rebuild from scratch?

3. Support for Airport cards...  Is it there?

4. What overall impressions have you had with a similar setup...

Thanks in advance, and I look forward to moving along with this change over.

-Readis

---

### Post by Len on 2005-04-08
1. Yes, you can.
use
```
fdisk -l /dev/hda
``` to list the partitions on your disk (if you have multiple disks the others will be called hdb, hdc, etc). Identify the OS X partition (here it is hda5) and use this:
```
sudo mkdir /mnt/macos
sudo mount -t hfsplus /dev/hda*x* /mnt/macos
```
to mount your disk at the /mnt/macos folder. Navigate to that folder to see your OS X drive. Of course you can set to automount it at boot in your fstab file and place it onto the desktop so you can avoid the dreaded terminal :).

2. If you mean, deleting partitions and creating new ones without wiping all partitions on the HD, yes you can. Actually that application is launched during the install. If you want to resize your HFS+ partitions, no. You can use a Mac OS tool to do this though and then let Ubuntu create partitions in the freed space.

3. As far as I have read the forums, Airport Extreme cards are unsupported :(.

4. On my 5500/275 Ubuntu works awesome, except that the 832x768 resolution isn't working, unless forced in a kernel argument. Not a problem for your powerbook.
My PowerMac G4 MDD 1.25 GHz suffers from bad audio due to alsa, but it works great (and FAST, faster as a 3 GHz pentium with the same amount of RAM) otherwise. OS X still beats ubuntu in speed at some parts though.

If you happen to have two partitions and you want to delete one, or are able to resize a partition in Mac OS, what keeps you from trying :P? Just make sure you do not wipe the wrong partition! You can always easily revert back to MacOS without wiping your HD. Just use the Ubuntu boot CD to wipe the Ubuntu partitions and create a new partition (or enlarge another) from within Mac OS.

---

### Post by philcolbourn on 2005-04-10
no free partitioning tools that I know of. there is a comercial tool, but one reviewer that used it said it ruined his osx partition, so i wouldn't use it anyway.

I just copied my data to cd and reinstalled osx at which point you can repartition the drive.

apple provide a way of using existing data but I have not tried it yet.

trackpad also does not work. you will need usb mouse.

I think there are some usb 802.11g cards that work, but I am not sure. the inbuilt airport extreme is not supported.

Apart from boot and work in a console, I can't say any more about how it works until i get a usb mouse.

---

### Post by jaymacwade on 2005-04-10
I have a 1Ghz iBook G4, and began my Ubuntu experiment w/ Warty.  I had tried some other PPC Linux distros on an older ibook, and Mandrake 10 and Gentoo on this one.  With Ubuntu, it took some tweaking to get DVDs to play smoothly, but the sound still wasn't sync'd with the video.  

Further tweaks allowed me to get MOL (OSX) working, and read/write access to the OSX partition, but lack of a working wireless prevented me from making it my everyday working OS over Panther (OS X 10.3).

Updating to Hoary was my attempt to get external VGA, but even after updating, it was not working.  I then reformatted the partition and installed Hoary from scratch shortly after it was released.  I thought that perhaps the update had carried over a display setting preventing the ext. VGA.  Hoary was reputed to 'just work' with external displays, but that hasn't been the case for me.  I now have the console cloned on the built-in and external displays, and achieved some progress, but X is still not displaying properly on the external.

Airport Extreme support is still in development and showing signs of (slow) progress.  I've tried a couple 802.11 USB adapters without success.  (Ndiswrapper doesn't work on PPC architecture.)  I'm still waiting to receive my D-Link DWL-122.  This is only a 802.11b adapter, but is reputed to work by other PPC Linux users on web forums.

x86 Linux is making strides toward becoming an OS useful to beginners as well as ubergeeks, but PPC Linux is not as mature and still catching up.  I would consider PPC Linux the domain of the savy, not for the feint of heart.  Use at your own risk!

jwade

---

