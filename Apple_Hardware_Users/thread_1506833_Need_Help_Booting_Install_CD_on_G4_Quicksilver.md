---
title: "Need Help Booting Install CD on G4 Quicksilver"
date: 2010-06-10
forum: Apple Hardware Users
---

### Post by bobbic on 2010-06-10
First, the problem; I'll give specifics after that.

The problem: I'd like to install Ubuntu 10.04 on my G4 Quicksilver. I can't seem to get the install cd to boot. I've tried holding "C" during restart, but that doesn't work (it just boots from my main drive). I tried command+option+shift+delete, but that doesn't work either. I tried booting from open firmware, per the official instructions (boot cd:,\install\yaboot), but I got an error. When I type in *boot cd:,\install\yaboot* and press enter, it says "load-size=0 adler32=1", then "Load-size is too small".

I'm feeling a bit silly at the moment...I don't understand what that means! So, if someone could tell me what that means, what I'm doing wrong, and how to fix it, I'd be a very happy girl!

Specifics:

Hardware Overview:

  Machine Name:	Power Mac G4
  Machine Model:	PowerMac3,5
  CPU Type:	PowerPC G4  (2.1)
  Number Of CPUs:	1
  CPU Speed:	867 MHz
  L2 Cache (per CPU):	256 KB
  L3 Cache (per CPU):	2 MB
  Memory:	1.25 GB
  Bus Speed:	133 MHz
  Boot ROM Version:	4.2.3f1


I have two hard drives installed. The first is my OSX drive, the second will be my Ubuntu drive. Here's the info on the second drive:

ST360015A:

  Capacity:	55.9 GB
  Model:	ST360015A
  Revision:	3.31
  Serial Number:	3KC1E4QC
  Removable Media:	No
  Detachable Drive:	No
  BSD Name:	disk1
  Protocol:	ATA
  Unit Number:	1
  Socket Type:	Internal
  OS9 Drivers:	No
  S.M.A.R.T. status:	Verified
  Volumes:
Chronos:
  Capacity:	55.77 GB
  Available:	55.75 GB
  Writable:	Yes
  File System:	HFS+
  BSD Name:	disk1s3
  Mount Point:	/Volumes/Chronos

Here's where things might get tricky: Over the weekend, the dvd portion of my superdrive kinda died. It still reads dvds (burned or commercial), but it won't write them anymore. So, thinking that my spare (from a later model G4) was also a superdrive (but not having the brains to check it first) I swapped them. Turned out it was just a cd drive. However, I have no problem burning the iso file and verifying, and I can see the disc on my OSX desktop. Here's its info:

LITE-ON LTR-12102C:

  Firmware Revision:	RAVD
  Interconnect:	ATAPI
  Burn Support:	Yes (Apple Shipped/Supported)
  Cache:	2048 KB
  Reads DVD:	No
  CD-Write:	-R, -RW
  Burn Underrun Protection CD:	Yes
  Write Strategies:	CD-TAO, CD-SAO
  Media:
  Media Type:	CD-ROM
  Blank:	No
  Erasable:	No
  Overwritable:	No
  Appendable:	No


So, what am I doing wrong, and what do I need to do to make it right? (And sorry for the long post...I've noticed that you all keep having to ask for specs every time someone posts a question, so I thought I'd beat you to the punch.)

Thanks!

---

### Post by linuxopjemac on 2010-06-11
```
boot cd:,\\:tbxi
```

---

### Post by bobbic on 2010-06-11
Thank you for the suggestion! I'd tried *boot cd:,\\:tbxi* previously, but I got the "load-size is too small" error.

I just tried re-burning the iso file, this time using Burn, instead of Disk Utility. I tried all of the things I had with the previous disc, with largely the same results. However, this time *boot cd:,\\:tbxi *brought me to a light gray screen with a darker gray "no" sign (the circle with a slash through it, like on a no-smoking sign). Nothing else happened after that.

Right now, I'm calling that progress...at least **something** happened! But I'll keep working at it...I'm determined.

---

### Post by linuxopjemac on 2010-06-12
I can't help you directly about this one, because I don't have a working CDROM module in my Pismo. I suggest you trying to boot in the same way USB booting works.

See "Booting the USB stick" in the following thread and replace usb by cd:
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc#1)

---

### Post by bobbic on 2010-06-12
Cool...thanks! I'll give that a shot. I'll update as I try things.

I did some more reading last night, and I noticed that booting from the install cd has been a problem with G4s on earlier releases. I didn't see any fixes other than things I've already tried here, but that made me feel a little less stupid. I did try a fresh burn of 9.10 last night, with the same results I've had with 10.04. Sometimes the most obvious solution is the one that will work, so I'm going to pick up a cd drive cleaner while I'm out today. I'm hoping that it's just something silly and simple like a dirty drive. But, in the spirit of "hope for the best, prepare for the worst," I've downloaded the alternate iso files for 10.04 and 9.10. That might work, too. But, as I said, I'll update and let you know what finally works (because, darnitall, it WILL work eventually...I'm determined)!

Thanks again!

---

### Post by linuxopjemac on 2010-06-12
You can always opt for a netboot installation. That's how I install Linux on my old Pismo without CDROM.

[http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

See my link how to do that.

---

### Post by Trooper1420 on 2010-06-16
The CD may not be burned in such a way that the Mac can see it as a  bootable disc.

I just installed 10.04 Lucid Lynx on a G4 Mirror Door Mac and had a lot of trouble creating a bootable CD. I hope the following information can help you out.  

First, a Windows machine is not the best thing for trying to create a CD that will boot on a Mac. I&#7743; not saying it absolutely cannot be done, but I haven't ever seen it work.

So, you'll need to download the install file onto a Mac and use the Apple Disk Utility to burn it to a CD like so:
  
[B]Drag  the downloaded .iso file to the left column of Disk Utility.  

Hit the  burn button & *then* insert a blank disc.[/B] (If you insert a blank cd first, you don get the ´burn' option) 
A slightly more complete chronicle of my efforts, which involved a bad disk  writer, is posted in [this  thread.]("http://ubuntuforums.org/showthread.php?p=9464535#post9464535")

Best of luck to you! Let us know what finally works for you!

---

### Post by bobbic on 2010-06-23
Sorry for the long delay...other things needed attention, so I had to set this aside for a few days. 

I finally have the install cd booting...at least, the alternate. The live disc boots but I just get a blank screen after getting through the initial command screen. The problem turned out to be my superdrive. It was dirty. It seems that my dvd-burning issues are resolved as well. I'm happy about that.

Now I'm hitting a new snag: the alternate install just grinds to a halt when it starts detecting hardware. I let it go last night, hoping it would do something exciting while I slept, but still nothing. 

No big deal...I'll get it figured out. I'll research this new problem, and I'll make a new post if (or maybe when?) I get stumped again!

Thanks again for your suggestions! I really appreciate it!

---

### Post by ethanay on 2012-09-27
I'm curious what the boot parameters were that allowed a successful boot from the alternate install cd?

---

### Post by Perfect Storm on 2012-09-27
This is an old thread. Please start a new one, thanks.


Closed.

---

