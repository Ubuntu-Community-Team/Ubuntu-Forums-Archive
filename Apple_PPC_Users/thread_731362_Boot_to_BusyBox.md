---
title: "Boot to BusyBox?"
date: 2008-03-21
forum: Apple PPC Users
---

### Post by systemarpi on 2008-03-21
Hi, I have just installed Kubuntu 7.10 (Alternate CD PPC), the installation after some problems ([http://ubuntuforums.org/showthread.php?t=731059](http://ubuntuforums.org/showthread.php?t=731059)) could be done successful.

But in the first boot try I get this message:

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules  ls /dev
ALERT! /dev/hda3 does not exist, Dropping to a Shell

Then... that gives me a BusyBox 1.1.3 shell

but.... I really don't have idea what to do next, this is my first Linux install under a PPC Architecture

---

### Post by slacka-vt on 2008-03-21
Busy Box is a kernel shell.
The filesystem is not found.
Did you install a boot loader ?
Yaboot seems to be most stable
for PPC architecture.
IMHO, Busy Box has been the biggest pain in the A$$ problem.
You need to make sure you have a complete kernel that's supported on your architecture.
The boot loader, Yaboot should be configured.
This process creates some kind of initramfs-boot image type thing (spl) *forgive my ignorance* 
That loads the kernel modules and makes your system hardware available for the OS to load.
I hate to sound like a broken record but:

Dapper and Hardy are the only officially supported Ubuntu PPC releases.
For novice users (myself included), this means something.

Stop trying to install Ubuntu distros on PPC's that aren't supported.

Hardy works great ! Of recently, has become a headache free install,
and most of all, it will be supported on the PPC architecture.

~s

---

### Post by stream303 on 2008-03-22
> **systemarpi said:**
> but.... I really don't have idea what to do next, this is my first Linux install under a PPC Architecture

Unfortunately, Linux on PPC sometimes isn't always plug n play, and can easily frustrate someone new to the platform.  Let's see if we can get you going.

Here's a quick list of things that would help us better:

What model / make of Mac are you using?  How much memory does it have?  Has it been modified with non-original components such as larger hard drive, etc?  Here is a good site to help inventory your hardware:

[http://www.everymac.com/](http://www.everymac.com/)

Since this is your first experience, I'd probably recommend the Feisty 7.04 "alternate" installation.  The amount of ram you have might make you lean away from Ubuntu towards Xubuntu, which uses less ram.  Once you get an easier install under your belt, you may want to upgrade or reinstall a more recent version later.  Gutsy has known issues that are just a pain to deal with for first-timers.

You can get Xubuntu Feisty 7.04 here:

[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/)

Sounds like you've got burning the iso image down, but just in case, burn at a lower speed, at least something that your mac's cd drive can handle, and maybe even lower than spec due to age, dirt etc.

With some new specs, let's see if we can get you up and running!

---

### Post by systemarpi on 2008-03-22
> **stream303 said:**
> 
What model / make of Mac are you using?  How much memory does it have?  Has it been modified with non-original components such as larger hard drive, etc? 

Firs... thanks a lot for your help... now, the specs are:

([http://www.everymac.com/systems/apple/imac/stats/imac_333.html](http://www.everymac.com/systems/apple/imac/stats/imac_333.html))
iMac G3
Processor: PowerPC 750 @ 333 mhz
RAM: 32+32 mb (I am not sure if thats from factory, maybe just the half)
HD: 6.0 gb*
Video: Ati RPT 6mb (vram)

*Since I remove Mac OS 9.1 I have all the space available in the case that matters

> **stream303 said:**
> 
Since this is your first experience, I'd probably recommend the Feisty 7.04 "alternate" installation.  .  Gutsy has known issues that are just a pain to deal with for first-timers. 

Yes.... Gutsy looks that was a wrong choice, I have downloaded Xubuntu 6.1, because that was the last official soported, should I give a try? or Xubuntu 7.04 is really the best first-timer option?


> **stream303 said:**
> 
Sounds like you've got burning the iso image down, but just in case, burn at a lower speed, at least something that your mac's cd drive can handle, and maybe even lower than spec due to age, dirt etc.
 

I checked the md5sum of the ISO, and the md5sum of some individuals files of the CD (I don't know how to check all files at once (once burned))

And then, at boot I check the CD with the &#8220;check&#8221; (easy to guess isn't it? hehehe) command, and everything was successful

If theres another integrity test I should know, please tell me.

Once again... thanks a lot

---

### Post by yellowbeard on 2008-04-12
any luck with your install i am having the very same problem.  Xubuntu 7.04 on a PPC G3

---

### Post by avtolle on 2008-04-12
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) might be helpful.

Have you tried typing (at the BusyBox prompt) modprobe ide-core, then when the prompt reappears exit to see if it continues to boot?

---

### Post by slacka-vt on 2008-04-12
Nope, I can verify that running:
 ```
modprobe ide_core
exit
```

yielded 
```
fatal: no modules found
```

this is what I posted on another thread
> Personally, I think there's a bug in the new powerpc kernel.
My ability to boot into my Mac OS X partition vanished literally over night.
I can still access my Macintosh HD but I can't boot the OS.

At the same time, my Hardy install, which has run flawless, booted into BusyBox.
This coincides with the linux update 2.6.24-16 yesterday.
After force restarting my system I was able to boot into Ubuntu but my yaboot.conf
was completely wiped out (like over-written almost ?)

very strange
~s

---

### Post by avtolle on 2008-04-12
I've not tried installing Hardy Beta, but yesterday, running from the Live CD (I'm one who wants to see if the thing will run before installing), had no success, regardless of what boot parameters I tried. When I got to a terminal, it was hanging at "Installing Local Boot Scripts" as I recall. There was also an error message about USB, but I forget what it said exactly.

G4 Cube, as I think I've posted before; stock everything except added RAM, and a USB floppy drive (don't ask why).

---

### Post by crapple on 2008-04-14
I had the a similar problem with getting Ubuntu 7.10 to load on my computer.  Hardy loads no problem except I am having trouble with my graphics card.  So it is not working on my computer but it doesn't get stuck in the busy box.:KS

You might want to try a fresh install of hardy beta if you have no important files on your computer.

---

