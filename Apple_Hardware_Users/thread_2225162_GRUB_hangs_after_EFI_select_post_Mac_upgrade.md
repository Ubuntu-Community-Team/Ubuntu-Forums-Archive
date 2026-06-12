---
title: "GRUB hangs after EFI select post Mac upgrade"
date: 2014-05-20
forum: Apple Hardware Users
---

### Post by DjBones on 2014-05-20
Hi, I'm having some issues with a dual boot Ubuntu 12.04 and Mac OS X 10.9.2 on a Macbook Air 5,2 (2012 13"). I had originally installed the Ubuntu partition according to the instructions on the Ubuntu wiki using rEFIt to manage the boot process. Everything worked out great after a little bit of work. However, recently, after updating Mac from 10.8 to 10.9, it overwrote something in the MBR which made the Ubuntu partition unbootable. At this point I went through a series of steps from material I found on the wiki and forums, probably mucking things up even more.

  * Upon updating Mac from 10.8 to 10.9, selecting the Ubuntu partition at boot in rEFIt gave "No bootable device"
  * I updated the MBR using the menu option in rEFIt, this resulted in a similar problem but now "Missing operating system". It looks like it took away the boot flag from my sda5 partition (sda4 is swap) and gave it a "msftdata" (?) flag instead.
  * I used a Ubuntu live USB environment to set the sda5 partition back to "boot" in gparted, this gave "No bootable device" again (maybe, hard to remember).
  * In the live USB I reinstalled GRUB from within a chroot environment, back to the "Missing operating system"
  * In the live USB I used the "Boot-Repair" program to reinstall GRUB, still same as above
  * I installed rEFInd with the "install.sh" script, removing that one file for bless'ing. rEFInd found two new boot options made by Boot-Repair, the first a windows loader, the second a Ubuntu loader. The Ubuntu loader now loads a working GRUB! However, selecting any of the GRUB menu options, ie from newest kernel, to older kernels, to recovery mode, results in a hang within GRUB. The text wipes, leaving the Debian background, and hangs. Changing the GRUB options like "quiet splash" to "debug nosplash" have no effect. Could there be a problem unique to the Macbook Air 5,2 hardware with something like "nomodeset"? I don't remember my original boot flags. I've tried "noapic nolapic nomodeset i915.i915_enable_rc6=1" to no avail.

Here is the output from Boot-Repair on my system: [http://paste.ubuntu.com/7490818/](http://paste.ubuntu.com/7490818/)

I use my Linux side for work, and setting it back up again would take quite a bit of finagling, the data is not so much the problem. I would be very happy if anybody here could help make the system bootable again. :) Also, I'm sorry if this is a mish-mash of a bunch of existing forum posts and things in the sticky, but my current efforts haven't paid off much.

---

### Post by oldfred on 2014-05-20
While the author of rEFInd says the UEFI spec allows two efi partitions, no UEFI systems currently work with two efi partitions. You have an efi partition with efi boot files in sda1 and a boot flag on sda5 which really is a data partition and has no efi boot files. Best to remove boot flag from sda5.

I do not know Mac and whether it just boots Ubuntu with UEFI or you have to have the chain load to a grub in a partition, but most systems do not have grub in a PBR or partition boot sector.

---

### Post by DjBones on 2014-05-20
Thank you for the response! I used gparted to remove the sda5 boot flag, now it has no flags. I'm not sure exactly what's going on, but my previously working setup had rEFIt load grub when I wanted to boot Ubuntu. The old menu entry that I used to boot Ubuntu with still says "Missing operating system". I've tried reinstalling grub with some new settings, namely selecting the Secure Boot option, and installing grub to sda1. I can load grub from the new rEFInd menu entry, but it hangs after selecting one of the options. I can't get any debug information out of it, so I'm not sure what's going on with grub.

Here is a paste of the recent run of Boot-Repair: [http://paste.ubuntu.com/7495302/](http://paste.ubuntu.com/7495302/)

---

### Post by oldfred on 2014-05-20
I do not know Macs, I just jumped in on one obvious error.

You are running a hybrid MBR/gpt drive. It was my understanding that you only need that to boot Windows as Windows will not or did not boot in UEFI mode on a Mac, so you have to configure it for BIOS/MBR boot. But Ubuntu will boot in UEFI mode on a Mac and works with gpt partitioning.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

It also is my understanding that rEFInd is an updated still maintained version of refit.

 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]
 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)

[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

### Post by Vinodh Moodley on 2014-05-23
I installed Ubuntu on my MacBook Air 2013 using the 64bit non-Mac iso via USB. Once it's installed, boot into OS X, mount your EFI partition and bless grubx64.efi. After this, holding the option key on boot will allow you to choose between Ubuntu or OS X. There is no need for rEFInd.

---

### Post by DjBones on 2014-05-25
Thanks Vinodh, you're right, I did not need rEFInd/rEFIt. Since the boot-repair program had already blessed the grubx64.efi, it's accessible through the "option menu" at boot like you say.

I figured out that the problem with grub halting is a kernel issue. When selecting a (specific) older kernel, I can boot back into Linux! However the broadcam wifi driver (Broadcom 802.11 Linux STA) does not work anymore. The "Additional Drivers" program `jockey` says that it fails to load. The log report in `/var/logs/jockey.log` has:
```
bcm43xx: blacklisted, b43: blacklisted, b43legacy... (other debug messages)
```
I also have a module called mac80211 or mac80211_hwsim but it doesn't seem to load.

I have a feeling that all of this is related to making the decision at one point to stay on the kernel 3.2.* branch because that's what worked with the mactel-support-ppa-precise repository and the specific drivers I already had installed. The newer kernels were supposed to support many things out of the box, but something had originally gone wrong, so I stayed on / pinned kernel 3.2.0-44-generic. Selecting the newest kernel I have installed, 3.3.6-030306-generic results in a hang at grub (probably found by boot-repair and set to default).

Should I open a new thread? Since this is a different question now, and not related to the original grub issue. I would like to get my wifi driver working again, and then, upgrade to a working newer kernel so I don't have this fragile system of drivers on an older kernel.

---

