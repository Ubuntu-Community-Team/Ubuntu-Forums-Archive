---
title: "Some problems installing Ubuntu Mate 15.04 on iMac G5 PPC"
date: 2015-05-06
forum: Apple Hardware Users
---

### Post by clkndk on 2015-05-06
My brother bought an iMac G5 ( PowerMac 12.1 , PowerPC G5 (3.0) ), 1.9Ghz, 1Gb memory, ROM: 5.2.6f1 with OSX 10.4.26 (or something similar, this number is from memory).
He came to me to set it up, the last owner had made an empty root user and left it like that.
So I made a new user for him and after some searching put another browser on it to make it work somewhat, but it is quite outdated.

Now my brother was convinced that installing Linux on it was the only way to make it current.

I downloaded the powerpc-iso of Mint Mate and first tried burning this on the iMac itself which failed, don't know why, perhaps a dvd with to high a speed.
Then I burned the dvd on another pc and booted from that, but the boot was hit and miss and it wasn't possible to start an installation.

After doing some searching I decided to go the usb route.

Using my Linux Mint laptop I put mate on my usb ( dd if=ubuntumate1504ppc.iso of=/dev/sdb ) (not exact command, didn't write it down).

Now for booting I put the usb stick in a usb of the iMac and started the iMac while holding down Ctrl-Alt-O-F which start to the open firmware prompt.
I found that my usb was at /ht&0/pci@2/usb@b/disk@2.
dir ud:2,\ showed my usbstick-directory.
I booted like this:
boot ud:2,\install\yaboot
Then at the next promt I choose: live
Now my live Mate environment started with a few remarks.
It says something about the size of my partition being wrong and something about Apple_HFS.

When it starts up the colors are a bit off, wireless isn't recognized and the fan is quite noisy.
Opened a Mate-terminal and did: sudo gparted
From gparted I was able to resize the OSX-partition from 150 Gb to about 100 Gb, so I had 50 Gb free, make a 2Gb swap partition and use the rest as Mate partition.
This took a while, but was succesfull.
Then I started the install and choose: something else ... when asked for partitioning because I didn't want the OSX-partition to be corrupted.
I choose to use the new partition as /.
Installation went flawless except at the end.
The end remark was that the yaboot bootloader didn't install properly and about the bootstrap partition it said: Apple_HFS should be Apple_Bootstrap .
After that I shutdown but when rebooting it just started OSX and my Mate-install was not available.

I have done some searching in this forum and already have some things to try.

But I have a few questions which would make the rest of my testing easier:
- DOES the Mate install fully support the hardware from this iMac or is Lubuntu or stock Debian better for this machine?
- what is the easiest way to make this installation boot without corrupting my OSX?

---

### Post by rican-linux on 2015-05-06
I would use 14.04, 15.04 has a lot of bugs on PPC.

---

### Post by Droidmaster909 on 2015-07-09
I'm really quite dissappointed with the fact that there's no real answer to this...  I have an iMac G5 and I have been trying to figure out a way to get Ubuntu MATE running on it... I too have the same issues, including the color problem... Does anybody at all have any help? This thread is one of the first things that comes up when you search for a solution..

---

### Post by rican-linux on 2015-07-09
Here is the current situation with Ubuntu and PowerPC. As of today 14.04 the most recent version of Ubuntu that works on PowerPC. So Lubuntu 14.04 and Ubuntu-MATE 14.04 are your options. 15.04 comes with xorg-core 1.17.1. This version contains a bug that distorts the DE. It has been documented thoroughly in this **[thread]("http://ubuntuforums.org/showthread.php?t=2264322")**. The most recent version of xorg-core (1.17.2-1) has the fix and as of today is only available in Debian Sid. I have informed both Lubuntu and Ubuntu-MATE communities about this. I have word from the lead developer of Ubuntu-MATE that is working on getting this fix in the 15.10 release. Until then 14.04 is your best option.

---

### Post by Droidmaster909 on 2015-07-10
ah, Okay, I understand now. 
See, the thing is that I had assumed that it was some sort of Display Driver issue, not that it was a bug in xorg itself. I was going crazy trying to figure out the problem! I tried different xorg.conf files, and tried a whole bunch of various things.
Thanks so much for the help, I genuinely appreciate it.

---

### Post by rican-linux on 2015-07-10
No worries, glad I can help. I need to update the known issues page with this info. I will try and get that done this weekend.

---

### Post by Droidmaster909 on 2015-07-10
I certainly hope i'm not hijacking this thread, but I seem to be running into a problem with 14.04 as well..
It doesnt seem to want to advance past these (see attached)

The list of starting/stopping appears after I click one of the arrow keys on the other screen

---

### Post by rican-linux on 2015-07-10
enter these at boot

```
live radeon.modeset=1 video=offb:off video=radeon:off radeon.agpmode=-1
```

---

### Post by Droidmaster909 on 2015-07-11
Perhaps i'm doing something wrong.. now im only getting that second screenshot (the one with the "call trace"s and such..

Pardon my lack of knowledge on the subject, but what do each of those commands mean anyway? I'm just curious to know.

---

### Post by rican-linux on 2015-07-11
Can you verify for me what video card the iMac has?

---

### Post by Droidmaster909 on 2015-07-11
ATI Radeon 9600, according to the machine itself

---

### Post by rican-linux on 2015-07-11
Hmm from I could see on google it could the error you are seeing is a result of bad ram.

---

