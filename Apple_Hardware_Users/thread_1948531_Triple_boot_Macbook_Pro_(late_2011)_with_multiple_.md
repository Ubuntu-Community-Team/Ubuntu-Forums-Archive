---
title: "Triple boot Macbook Pro (late 2011) with multiple disks"
date: 2012-03-28
forum: Apple Hardware Users
---

### Post by msarro on 2012-03-28
Hey everyone. I am trying to find a workaround which will let me install OSX, windows 7, and ubuntu in my macbook. As OSX will be the primary OS, I plan to keep the primary hard disk dedicated to it (its a 120GB SSD). I am looking to purchase a data doubler and remove the optical drive - swapping a 750GB 7200rpm hard disk in its place.

What I would like to do is pull out the SSD that has OSX, and put the new 750GB HDD in. Then, install windows normally to that disk, configuring approximately 1/4th to be used for windows 7. Then, using the next 1/4 for ubuntu, and setting GRUB to be installed on the windows partition (when the EFI bios sees the windows HD, when started it will prompt me for whether I want windows or ubuntu). The remaining disk space will be in some format that everything can read.

After this has been installed successfully, I will move that to the second bay of the macbook, and replace the OSX HDD.

First, does GRUB work with EFI out of the box? Are there any special considerations to take into account for when doing this? Will installing grub on to the windows 7 partition screw anything up?

Sadly rEFIt doesn't seem to work with multiple disks, so installing GRUB to the linux partition probably isn't an option.

Any advice from anyone who has done this would be really appreciated. Thank you.

---

### Post by msarro on 2012-04-03
As a followup, it does work.

I removed the solid state disk, and popped in the 750 gig disk. I then installed windows 7 (600GB partition). This installed with no issue.

Afterwards, I installed ubuntu by DD'ing the ubunutu 11.10 image to a USB disk. I also burnt the installer CD to physical media. From here I turned on the laptop while holding the "C" button. Next, I told the system I wanted to install Ubuntu. I had it install next to windows 7 (not overwriting anything).

Once this was done, I removed the CD drive, and the hard disk. I installed the 750GB hard disk in the data doubler. I then replaced the solid state disk in the primary slot. I reattached the bottom of the laptop, held the option key, and turned on the laptop's power.

I was presented with a MacOS bootable disk, and a "windows" bootable disk. After selecting the windows disk, you are presented with the GRUB boot loader. I have now verified that both Linux and Windows are bootable at this point. So, happy joy, it is working exactly as I want! The only downside I've found is that the enclosure I got for the (now) external cd drive requires two usb connections to power the disk. Sadness!

---

