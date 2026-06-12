---
title: "Failed to load X server..."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-07-14
Right.  Here's the problem.  I'm currently getting one of my friends into Ubuntu.  He has an Nvidia Geforce 8800. 

Problem is, whenever I load the Nvidia driver (yes, I have the right 8800 driver) it complains that it's failed to load the X server when it boots. It then goes to command line.  When I reset it back to a previous version, it's fine.

Any help on how to solve this?

I've had similar problems like this on at least 3 computers. On one, I reinstalled Ubuntu and it was fine, but this time it didn't work.   


Oh yes, it's Ubuntu 7.04 Feisty Fawn.

---

### Post by starsky on 2007-07-14
hi there :)
when you get into the console mode, do this -

sudo dpkg-reconfigure xserver-xorg

for howto, you can look it up here -
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

remember to set proper device driver ("vga" is the most generic device driver that is guaranteed to work).

Just go through that howto and you should be fine. :)

do post back.

HTH

---

### Post by Neon_Knight on 2007-07-14
Yeah, I tried that, but I selected "nvidia" as the driver.  Problem is, without the Nvidia there isn't any 3d accelleration for gaming etc.  Which was the whole point of installing the drivers in the first place.

---

### Post by starsky on 2007-07-14
yeah, try this then -
[http://ubuntuforums.org/showthread.php?t=421376](http://ubuntuforums.org/showthread.php?t=421376)

---

### Post by starsky on 2007-07-14
Also note that there are binary drivers (no source code available) available for nvidia. this issue has been discussed many times in this forum -
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
Googling also helps. :)

---

### Post by Neon_Knight on 2007-07-14
> **starsky said:**
> yeah, try this then -
[http://ubuntuforums.org/showthread.php?t=421376](http://ubuntuforums.org/showthread.php?t=421376)

Yes, the problem with that is that I don't actually know what the problem is. It just won't start the X sever with the nvidia drivers installed.

---

### Post by heldal on 2007-07-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The problem for 8800 gpu owners is that there's a file missing from the nvidia-drivers as packaged for ubuntu. 8800 gpus (GTX and GTS) require an extension-module for the X-server that is supplied by nvidia in the form of a pre-compiled/linked shared library libwfb.so. This file should have been included in the nvidia-glx-new package, but hasn't made it there despite this problem being known since mid April (according to bugs reported to launchpad). Workarounds exist, but ... unless you're willing to jump a few hoops ubuntu is not for 8800 owners.     

Try to search for "libwfb" in the forums for workarounds.

It isn't always easy to determine if something should be a bugfix or delayed to the next revision. Yet, considering the extent of the problem with nvidia-drivers in feisty my suggestion to the maintainers would be to issue updates to feisty that:

1. Stop trying to separate different versions of the driver (legacy,current,new) through various (imho broken) scripts. Just make the packages mutually exclusive and make sure only one version gets installed on a machine. Now it's a mess, and there are even empty files place in the filesystems used to flag which version is installed that don't get removed as part of the package. 

2. Include _all_ driver components supplied by the vendor. That would of course include the wfb x-server module which is now missing from the nvidia-glx-new package.

3. Preferably also swap to a more recent version of nvidia's driver as the one currently used (1.0.9755) has a couple serious bugs (freezes in 3d processing). That would also enable support for the 8500 and 8600 budget-gpus which are currently shipping in large volumes

---

### Post by Neon_Knight on 2007-07-16
Oh, I see.  Thanks for the info.


Do you know of any alternative drivers that may allow 3d acceleration on Nvidia cards?

---

### Post by heldal on 2007-07-17
> **Neon_Knight said:**
> Oh, I see.  Thanks for the info.


Do you know of any alternative drivers that may allow 3d acceleration on Nvidia cards?

There are no alternatives that support hw-acceleration and there won't be until vendors release complete hw specifications. 

Don't get me wrong. Nvidia does at least allow redistribution of their drivers so they can be packaged in a distro.
They've got a much better track-record on non-MS platforms than ATI in recent years and work just fine (even the 8k models) with x.org on any current linux distribution. It's unfortunate that driver packaging was messed up in ubuntu 7.04, but that is not make it a general problem wrt nvidia-support in x.org. It's not really hard to make x.org on 7.04 work with the 8800s. You just don't quite get there with the default install process.

---

### Post by dragonwings on 2007-07-17
sudo aptitude install nvidia-glx-new
above for latest nvidia drivers

sudo apt-get update

if you cant use 
sudo dpkg-reconfigure xserver-xorg 
try resarting pressing Esc 
then boot in recovery mode 
let it do its thing then try  sudo dpkg-reconfigure xserver-xorg 
should work.

---

### Post by heldal on 2007-07-18
> **dragonwings said:**
> sudo aptitude install nvidia-glx-new
above for latest nvidia drivers

sudo apt-get update

if you cant use 
sudo dpkg-reconfigure xserver-xorg 
try resarting pressing Esc 
then boot in recovery mode 
let it do its thing then try  sudo dpkg-reconfigure xserver-xorg 
should work.

Sure, but that isn't enough for 8800GTS/GTX users.

nvidia-glx-new is still missing libwfb.so (or some version thereof) without which the nvidia hw-accelerated x-server will fail to load on a 8800. To use the driver in nvidia-glx-new one must also download the driver from nvidia (choose according to cpu architecture), extract the missing file and place it in /usr/lib/xorg/modules

---

