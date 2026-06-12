---
title: "Mac Mini 6,3 12.04, working fine, then update borks system"
date: 2013-06-07
forum: Apple Hardware Users
---

### Post by ghetto2ivy on 2013-06-07
I'm running 12.04 on a mac mini server, and all was well until an update in the pat few days. Ran a regular kernel update (whatever came out this week 6/3) and restarted the computer. Now Ubuntu won't boot, can't even get to grub. I just get a blinking cursor.

Any tips on how to diagnose and fix?

The hardware is fine, it works in OS X.

---

### Post by MrSteve on 2013-06-07
had the same problem with a mac mini 
it seems that on install of a linux system it loads the EFI boot loader
but on a kernel update it fubars the system 

maybe reinstall and then install the grub efi bootloader, that may work
(never tried it) in the ubuntu software centre search for grub efi

but in the end i built a new small factor shuttle system to run linux ...

---

### Post by sandyd on 2013-06-07
moved to apple users

---

### Post by ghetto2ivy on 2013-06-11
I did manage to get the system back online, but only via installing 13.04. This right in line with  MrSteve's observation. 13.04 had the latest Grub EFI bootloader. If you do install 13.04.0 please note that the default install kernel doesn't have support the wireless or network card until an update is run. So have a backup usb network connection handy after install. After an update everything works off the bat except for video which requires some tweaking to get full color:
# intel_reg_write 0x70008 0xC4002000
# intel_reg_write 0x70180 0xDA004400

---

### Post by nknize on 2013-06-11
Guess I could have perused the latest posts... This sounds like the exact same problem I just ran into in post: [http://ubuntuforums.org/showthread.php?t=2153625](http://ubuntuforums.org/showthread.php?t=2153625)

My question for you is, did you fresh install everything?  Or can a simple reformat of a /boot partition do the trick?

---

### Post by ghetto2ivy on 2013-06-12
I was going to update to 13.04 anyway so I just went ahead and fresh installed everything. Well almost, kept my home and am going to restore my /etc selectively.

I suspect, if I had been really diligent I could have even used a grub repair to fix the issue.

---

### Post by nknize on 2013-06-12
Well... I tried a grub repair using boot-repair and that didn't seem to work either - but I'm also not a grub expert.

Here's the pastebin of the boot-repair [http://paste.ubuntu.com/5756512/](http://paste.ubuntu.com/5756512/)

After hours of struggling with that, I stumbled on [http://rodsbooks.com/ubuntu-efi/](http://rodsbooks.com/ubuntu-efi/) and started heading down this path.  Now I boot into refind, it finds both 3.0.2-35 and 3.0.2-45 kernels, neither of which will boot.  Tried Super Grub Disk 2 - also no luck... it finds the core.img and when I select it, it just reboots the system.

Any thoughts would be appreciated.  If not, it looks like I'll be imaging the drive and just reinstalling everything.  Are you booting 13.04 using rEFIt with hybridMBR or are you booting into 13.04 in EFI mode?

---

### Post by ghetto2ivy on 2013-06-16
This maybe too simple, but have you tried booting back into mac and editing which partition is booted from in rEFIt/rEFInd?
For me after a reinstall, I realized that I kept telling refit to boot my same linux icon, only to ignore a new icon (like a set of blocks) that was the 64 bit EFI boot (I beleive) for 13.04 and therefore working.

---

### Post by JoeBlack2k on 2013-07-12
You don't have grub (grub is MBR only ...) Grub-EFI is for EFI and your hard disk is GPT so it's EFI 

so Booting with grub-repair and such.. doesn't work

EFI Stub booting is not supported by kernel 3.2 it's not going to work


you need to boot Linux in legacy mode 
burn the grubsuperbootdisc to a dvd not usb
then hold ALT when booting and do NOT select efi but "Windows Disk" this makes the Apple boot into legacy mode and do bios emulation which boots kernel 3.0 or 3.2
the upgrade the kernel to 3.10 or 3.8 whatever

..then it works

---

