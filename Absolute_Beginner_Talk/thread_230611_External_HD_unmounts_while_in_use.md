---
title: "External HD unmounts while in use"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-06
Hi
Yesterday while playing music on RhythmBox, my usb hd unmounted itself after less than one minute.

I tried this over and over, including after rebooting, and the same thing happened repeatedly. (I actually posted here on this before I had diagnosed the failing media player as being due to the usb hd unmounting but received no replies to date).

While I was having this problem, I booted to WinXP and tried the music player there (wmp 11) which runs off the same usb hd. No problem at all here showing that it wasn't a problem with the external hd.

Interestingly, today everything is working fine again and I can run RhythmBox from Ubuntu for a long time without problems.

Can anybody help me explain what's happening here?

Thanks 
Paul

---

### Post by orb9220 on 2006-08-06
I Can't Believe! You fell for that old windows trick to get you back into windowsXP. And you fell for it. LOL

No just kidding and I havn't heard of that happening. But be sure to post if it returns. And I will keep my eye's open if I read about it agian.

Good Luck.

---

### Post by catlett on 2006-08-06
FYI, pmount controls mounting/unmounting of removable devices. There have been pmount bugs in the past. If it persists, make sure you have the latest pmount available and also make sure there isn't an entry in /etc/fstab for the drive. pmount doesn't use /etc/fstab. this shouldn't be an issue but in another thread the external was hooked up during install and it had am /etc/fstab entry. 
Long story short, the drive was not behaving correctly. We tried deleting the /etc/fstab entry so the system isn't trying to mount it at start-up and pmount alone will deal with the mounting. It worked. pmount mounts when the drive is powered on and unmounts without an issue.
In that case pmount solved the problem, although in this case it appears pmount is the problem.

---

### Post by PaulFXH on 2006-08-06
Thanks for your reply catlett

Yeah, none of my usb hds are included in fstab now and all partitions on them show up faithfully on the desktop after booting.

Now, while the media player (RhythmBox) has performed much better today it is still cutting out in unison with the drive partition icons disappearing from the desktop (and also from the System Monitor Devices section. The second occurrence happened as I was writing this post.
So whatever the problem is, it has not gone away.

My version of pmount is 0.9.11-1 which I believe is the most recent version.
Incidentally, a notification in the Synaptic dialog box seems to suggest that greater functionality of pmount is available if the Hal package is also installed. 
Here's what it says:

This package also contains a wrapper "pmount-hal" which reads some
information like device labels and mount options from hal and passes
them to pmount. Install the package "hal" if you want to use this
feature.

I don't have the Hal package installed but don't know if this could be contributing to this particular problem.
Additionally, I don't have either of the portable mount library modules installed, too.

Note that after the usb drive unmounts, just switching it off and back on again brings the icons back to the desktop and the media player works fine again.

I'd appreciate any comments

Thanks
Paul

---

### Post by catlett on 2006-08-06
hal might be it. Just for a comparison, I have hal imstalled and hal device manager etc, and I did not install them they were installed with the base system.
Just FYI here is what I have installed.This is the description for hal
```
Hardware Abstraction Layer
HAL provides an abstract view on hardware.

This abstraction layer is simply an interface that makes it possible to
add support for new devices and new ways of connecting devices to the
computer, without modifying every application that uses the device.
It maintains a list of devices that currently exist, and can provide
information about those upon request.
```
This is the description for hal-device-manager
```
Hardware Abstraction Layer user interface
HAL provides an abstract view on hardware.

This abstraction layer is simply an interface that makes it possible to
add support for new devices and new ways of connecting devices to the
computer, without modifying every application that uses the device.
It maintains a list of devices that currently exist, and can provide
information about those upon request.

This package provides a user interface which shows the information HAL knows
about the devices on the system.
```This is the entry for libhal1
```
Hardware Abstraction Layer - shared library
HAL provides an abstract view on hardware.
 .
This abstraction layer is simply an interface that makes it possible to
add support for new devices and new ways of connecting devices to the
computer, without modifying every application that uses the device.
It maintains a list of devices that currently exist, and can provide
information about those upon request.

This package contains shared libraries to be used by applications.
```And finally this is libhal-storage-dev
```
Hardware Abstraction Layer - shared library for storage devices
HAL provides an abstract view on hardware.
 .
 This abstraction layer is simply an interface that makes it possible to
add support for new devices and new ways of connecting devices to the
computer, without modifying every application that uses the device.
It maintains a list of devices that currently exist, and can provide
information about those upon request.

This library provides an interface for handling storage devices.
```
I would install hal. If I had to guess, these libraries will most likely get installed automatically when you select hal.
It's worth a try. I don't believe it will disrupt your system. I d I would install hal you can always uninstall it.

---

### Post by PaulFXH on 2006-08-06
Thanks again for the reply catlett

Now here's something very peculiar.
I went to Synaptic to install hal only to find that both it and hal-device-manager were both marked as being installed but I am 100% certain they were NOT marked as being installed when I checked about three hours earlier.
The machine had been rebooted about one hour prior to this startling discovery and may have had some influence on matters.

In any event, I also installed the two libhal packages you mentioned which were not installed.
However, within about 20 minutes of this manoeuvre, the drive unmounted itself for the third time today. So this wasn't the solution.

Incidentally, yesterday I reformatted one of the partitions on the Seagate usb hd from ntfs to ext3 (the music comes from another logical partition on this drive). I realize that this does not seem a likely culprit but given that no obvious solution is available, one is forced to look at more improbable possibilities.

Seriously puzzled
Paul

---

### Post by catlett on 2006-08-06
I don't know what to do. I agree everything has to be tried. I would use gparted live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) to look at the drive. See if it comes up with anything. If you don't have data on the partition you mightt won't to reformat it.
I would try uninstalling and then reinstalling pmount as well. 
You may even want to try using usbmount instead of pmount. I haven't used it myself but it is in the repository. Just search for "usbmount", it does the same thing mount/unmount usb devices
I would assume you have to uninstall  pmount and the hal packages.

I'm really baffled. I personally have a 160gb Seagate usb/external hard drive and I have no problems with it at all.

---

### Post by PaulFXH on 2006-08-06
Yeah, this is a real puzzle.
But if life was too easy, it wouldn't be much fun.
Actually, since my last post, I completely removed rhythmbox and then re-installed it. In addition, I loaded my music files from my other usb hd (this is the "back-up" in real-file format).
This has worked fine for over an hour, perhaps indicating that it's the Seagate drive that's the problem.
Nevertheless, as I said yesterday, this drive works fine when I boot to WinXP.

before I switched to the other drive, when the Seagate drive unmounted, I tried to mount it from terminal and got a message that the mount point didn't exist (although it must have existed 10 minutes earlier).
So I did a mkdir to create it again and then ran the mount command again.
This time i got the message:

> special device /dev/sda7 does not exist

So the partition with the music wasn't being seen...hmmm

I'll try the usbmount package and I may reformat the partition although it does have 35GB of music. However, it is backed up.

Thanks for your help so far,
Paul

---

