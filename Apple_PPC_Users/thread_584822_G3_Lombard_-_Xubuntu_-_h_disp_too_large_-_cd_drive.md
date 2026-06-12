---
title: "G3 Lombard - Xubuntu - h_disp too large - cd drive can't be found"
date: 2007-10-21
forum: Apple PPC Users
---

### Post by mikezila on 2007-10-21
I've had a love affair with Linux for years.  I really, really want to make it my solo OS, as it can do anything Windows can do, and better...save for play any of my commercial games decently.  I have an ATi video card, so anything more complicated than glxGears fails miserably.  Trying to run any game more recent than Doom via Wine, Cedega, or Crossover is blind suicide.  Anyways, I digress.

I thought I finally had a way to get a Linux system I could keep around without having to compromise on my old laptop, but it's giving me headaches.  I'm no stranger to the "headaches" Linux brings on, but this one has me stumped.

The Lombard is short of memory, about 160MB if I remember, not quite enough for Ubuntu I don't believe, but should be enough for Xubuntu.  I burned the standard PPC image, and it fails to busybox with "h_disp too large"  It makes it as far as the bouncy progress bar, then chokes to Busybox

I thought I would try the Alternate CD, and during the Debian installer it fails to find the CD drive.

I figure this shouldn't be too hard to fix, seeing as I see posts all over the place with people saying they got it working on a Lombard, but I don't see any of my particular issues.  Google doesn't bare anything useful either.

---

### Post by mikezila on 2007-10-21
Obscure error on obscure hardware.  I'm doomed.

---

### Post by oswaldkelso on 2007-10-23
No your not. Use the search facility for this section of the forum enter "lombard" or "pismo" I'm sure you'll find an answer. Try

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

if not debian works ;

---

### Post by mikezila on 2007-10-23
I've already done extensive googling and searching, no dice.

---

### Post by oswaldkelso on 2007-10-24
Here is a useful link 

[http://linux.bigga.de/index.php?lo=120](http://linux.bigga.de/index.php?lo=120)

leading the this 
[http://people.debian.org/~branden/ibook.html#run_installer](http://people.debian.org/~branden/ibook.html#run_installer)

which shows how to install debian via net in stall ...without using any physical media!,so no need to use a cd. Its for an ibook and "woody" not "etch" but I THINK the proccess is the same. You would need to goto the link below select:
"other images (netboot, usb stick, floppy, etc)" and ppc

[http://www.debian.org/releases/stable/debian-installer/](http://www.debian.org/releases/stable/debian-installer/)

Once you have debian installed you should not have a  problem installing any disto you like.

also it looks like there may be a different key combination for older power books try:
If holding  down the C key fails, try holding command-option-shift-delete and see if that works.

Also if it "old world" see this:

[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

---

### Post by Tommy on 2007-10-24
> **oswaldkelso said:**
> Here is a useful link 

[http://linux.bigga.de/index.php?lo=120](http://linux.bigga.de/index.php?lo=120)

leading the this 
[http://people.debian.org/~branden/ibook.html#run_installer]("http://people.debian.org/%7Ebranden/ibook.html#run_installer")

which shows how to install debian via net in stall ...without using any physical media!,so no need to use a cd. Its for an ibook and "woody" not "etch" but I THINK the proccess is the same. You would need to goto the link below select:
"other images (netboot, usb stick, floppy, etc)" and ppc

[http://www.debian.org/releases/stable/debian-installer/](http://www.debian.org/releases/stable/debian-installer/)

Once you have debian installed you should not have a  problem installing any disto you like.

also it looks like there may be a different key combination for older power books try:
If holding  down the C key fails, try holding command-option-shift-delete and see if that works.

Howdy -- those are all good links, but the command-option-shift-delete key combination is to reset the PMU (power management unit) -- slightly more extreme than resetting the PRAM (parameter RAM).

As far as I know, the C key would be the correct key to boot with IF the disk is bootable for that model. 

I believe the Lobmard was the first newworld PowerBook.  (My Wallstreet is one of the models just prior to yours and it's definitely an "oldworld," so it requires booting into MacOS and a utility called bootx to boot linux. There are other techniques to boot linux, but if you can stick with the yaboot bootloader that's standard in Ubuntu you'll be better off.)

BUT back to your issue. First, make sure you have the CORRECT TIME set on your internal clock -- you may need to boot into Mac OS to do that, but there's a known issue with some older models that won't allow things to load if the time has reset back to 1956 or 1904 whatever year it goes on that model. Then without removing the power, try booting the CD again.

FINALLY, be aware that Gutsy is not booting at all on a lot of models right now... when you get to the busybox you can modprobe the modules that are not (but should be) in the kernel and then resume the installation, and you have to be sure to add those modules to your initramfs. See this bug for details.

[https://bugs.launchpad.net/ubuntu/+bug/126337](https://bugs.launchpad.net/ubuntu/+bug/126337)

(Because you have an older model, there may be additional parameters the kernel needs to get started -- on my Wallstreet I have to pass a parameter to the kernel video driver -- your "h_disp too large" error sounds suspiciously relevant. You might try adding video=ofonly to the kernel parameters and see if you can get something reasonable on the screen. BUT that may be a "red herring.")

EDIT: I just noticed there are several recently updated posts in this forum about the booting problems with Gutsy, so see them for additional details. I believe there were similar issues even in Feisty. I know I was not able to boot my oldworlds with Feisty, and I haven't had time to try the latest version(s) of Gutsy -- knowing I will need to modprobe and build the initramfs with the missing modules to get it going.

---

### Post by oswaldkelso on 2007-10-24
HIi thanks for that. 
I'm in the proccess of getting an old 3400 powerbook up and running hence the links I've come across, this old pb needs bootx and this snippet was in the read me.

> WARNING !

BootX and  miBoot should be avoided on "newworld" type machines. Those machines are all the "colored" macs (iMac and later). Those machines should be booted via Open Firmware, using yaboot or an equivalent OF based bootloader. The only "newworld" machine that still requires BootX/miBoot for proper functionalities is the "**Lombard**" (101/bronze keyboard) PowerBook, at least until it's video driver is fixed.

I know this maybe out of date but It seems the lombard is (or maybe)  new world and old world. I'm wondering if all the problems people have been having with these on the change pb's is maybe to do with if the're coming from 0s9 or osx? and the " state" their previous os leavs them in?

---

### Post by Tommy on 2007-10-24
> **oswaldkelso said:**
> It seems the lombard is (or maybe)  new world and old world. I'm wondering if all the problems people have been having with these on the change pb's is maybe to do with if the're coming from 0s9 or osx? and the " state" their previous os leavs them in?

Technically, that's why the "experts" never liked the bootx utility -- it ditches out of OS9 in a bad way, somehow. HOWEVER for those of us still using it, it's much more direct than miboot. I believe miboot is/was to be the successor (and the "free" alternative) to bootx, and miboot doesn't require an OS9 installation. HOWEVER its installation procedure has been touchy. I believe it requires making startup diskettes, and the diskette driver in linux tends to make disks that aren't QUITE bootable on a Mac. So one tends to have to try multiple times to get a bootable diskette. AND you have to leave the diskette in the drive, which just doesn't "feel" right. Besides, on your Lombard, you may have something else in the bay. 

SO if bootx is usable with your Lombard, you might try it. It's actually fairly easy to try different linux kernel commands with it (because you're filling in a field in the boot program). HOWEVER, you will want to start with a kernel that you know will WORK with an oldworld, so that means going back to Dapper, or getting someone to post a initramfs file for a specific kernel that has the modules needed to get the oldworld to boot. 

I wish I had time to tinker with this now... I have my Wallstreet running Dapper, and a PowerMac 9600 that has been totally resistant to all versions of Ubuntu (and gentoo) that I've tried to start it with. I downloaded a beta image of Gutsy a few weeks ago but (as you know) it takes awhile to go through all the steps, and some other things have taken my time...

---

### Post by mikezila on 2007-10-24
This whole ordeal has proven to be much more trouble than the end result would be worth.  I would just be using it for Firefox and music anyway.

---

### Post by Tommy on 2007-10-26
For anyone following this thread, I mentioned "miboot" (the diskette bootloader used in Debian) but I believe the newer utility is called quik -- which I haven't used, either, but was intended to be the equivalent to yaboot for oldworlds.

If you can get quik working, upgrades should be MUCH easier than with bootx. With bootx is whenever you have a kernel and/or ramdisk update you have to mount the macOS partition and manually copy the files to it before rebooting. If quik works on your system I believe it updates the boot files automatically.

Of course with the Lombard, you may be able to get yaboot working with some Open Firmware magic -- start following links from [http://penguinppc.org/mac/](http://penguinppc.org/mac/) and I believe you will find the most comprehensive information about bootloaders at the NetBSD site.

---

