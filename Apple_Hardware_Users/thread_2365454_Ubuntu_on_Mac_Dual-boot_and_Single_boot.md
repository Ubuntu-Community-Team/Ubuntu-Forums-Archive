---
title: "Ubuntu on Mac: Dual-boot and Single boot?"
date: 2017-07-06
forum: Apple Hardware Users
---

### Post by sterator on 2017-07-06
Is there a place for me to begin reading how to achieve this on my Macs, both Intel macs?

I recently tried with Mint and had dismal luck succeeding with the installation. Things *appeared* to go very well during the installation procedure, only to fail massively upon reboot.

I created a dual boot of Ubuntu/OSX on a PPC Mac a few years back..I have *some* experience with things.

Thank you for any pointers!

---

### Post by QIII on 2017-07-06
Moved to Apple Hardware Users

---

### Post by johndough2 on 2017-07-07
Hi

Formatting is the first hurdle, subdividing the HDD.
A boot manager is the second.  rEFIt or rEFInd can be an answer.

Otherwise it should just be fairly routine, although you may want to try boot camp to create a partition/area that you can re-format to suit Ubuntu so that the Mac will acknowledge the presence.

rEFIt / rEFInd will allow booting from a USB or Disk so that a live version could tried out prior to installing, and with the knowledge of a live boot to clean up any unfortunate mess if it all fails.

---

### Post by kevin160 on 2017-07-08
My main "goof round with operating systems" computer is a mac, so I've done quite a few installs.   It currently multi-boots macos high-sierra, ubuntu 17.04, and vmware esxi.  

#1:  Backup any important data to a drive that your installation  and verify that your backup was successful.  

#2:  rEFInd and gdisk are your friends.    [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) and [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

The rest you can probably figure out on your own, but here are a few tips:  

There are 2 ways you can boot linux on a mac:  in bios/bootcamp mode, or in EFI mode.  I'd recommend EFI, since it's the native mode and you won't run into odd hardware issues.  There are guides at [http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot-short-version/](http://heeris.id.au/2014/ubuntu-plus-mac-pure-efi-boot-short-version/) and a thread on these forums with 32-bit efi workarounds (for older macs, probably not you) at [https://ubuntuforums.org/showthread.php?t=2287767](https://ubuntuforums.org/showthread.php?t=2287767) 

I've found a usb stick made with [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) to be really useful for installing linux since it will search disks for linux installs and let you boot them without having to fiddle with grub command lines to find partition designators.  It's easier to fix a linux boot from inside linux.  

Sometimes a new linux install, or a macos update, will reset your boot order.  If you create a secondary rEFInd partition as described at [http://www.rodsbooks.com/refind/installing.html#moving](http://www.rodsbooks.com/refind/installing.html#moving), when that happens you should be able to hold OPT and simply pick that rEFInd partition to get back to normal.

---

### Post by sterator on 2017-07-08
So are there step by step instructions to help a guy like me go from having a Mac that has OS X on it to installing Ubuntu so that when I reboot, I get to log into Ubuntu?

On this particular Mac, I want Linux and only Linux. Is it possible to do this? 

If so, are there easy to do instructions for a person who is new to the process, covering the ins and outs, what you need to be aware of and take care of, etc?

thank you!

---

### Post by sterator on 2017-07-08
Also, the Mac Pro in question is 4,1

I see links for 1,1  2,1   3,1   6,1  but bamboozlingly, there's none for 4,1!  Is this an unsupported mac pro?

---

### Post by Donnut on 2017-07-10
I've dualbooted the 4,1 before, and it's very easy. I suggest using bootcamp to repartition your drive, install Ubuntu via USB drive, then hold option upon rebooting to boot into your mac. Once there, install Refind. Done!

---

### Post by kevin160 on 2017-07-11
Mac pros work with current Ubuntu (17.04) all the way back to 1,1 models.  

It's been a while since I had only ubuntu installed, but my recollection is that you just install.  If the mac boot system can't find macOS anywhere, it will boot ubuntu.  

There will be a long pause (blank white screen) while it searches for macOS.  

You can eliminate this delay by "blessing" grub, or by installing rEFInd and blessing that.  You'll want to have an external boot drive with macOS installed on it to run the "bless" program.   

[https://help.ubuntu.com/community/UEFIBooting#Apple_Mac_EFI_systems_.28both_EFI_architecture.29](https://help.ubuntu.com/community/UEFIBooting#Apple_Mac_EFI_systems_.28both_EFI_architecture.29)

or 

[http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html)

---

