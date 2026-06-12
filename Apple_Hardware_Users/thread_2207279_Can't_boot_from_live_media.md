---
title: "Can't boot from live media"
date: 2014-02-22
forum: Apple Hardware Users
---

### Post by jorgeblasio on 2014-02-22
Hey everyone.

I've a 2007 Aluminum iMac, 24' with a 2 Tb HD and a 350 Gb Firewire 800 drive. Apparently the CD drive is busted and keeps rejecting every single disk I feed it.

I've tried running LiveUSBs and using the Firewire drive too as Live Media but I just can't get anywhere. With Unetbootin with the syslinux fix, I get to boot both Kubuntu 13.10 64bit and Mint Petra 64bit, but everything stops after a few minutes and I get dropped into GRUB with the error: 

BuzyBox V1.20.2 (Ubuntu 1:1.20.0-8ubuntu1) built-in shell (ash)
Enter 'help' for a list of built in commands.


(initramfs) unable to find a medium containing a live file system.

I've tried changing the boot parameters to direct it to sdb1 but I get the same results.

I also tried Mac Linux USB Loader and with my 8GB US drive the iMac just won't recognize it as bootable, and when using the firewire drive I get this error:

Welcome to Enterprise! Version 0.1
Distribution family (null) is not supported
Cannot continue because core files are missing. Restarting...

Any ideas?

---

### Post by jorgeblasio on 2014-02-28
C'mon, I can't be the only person with this problem...

---

### Post by entangled on 2014-03-07
I can't boot ubuntu on my iMac (21.5, mid-2010). Like you, all media is rejected.
My internal DVD has failed. An external DVD won't boot from DVD. 
The only (partial) success I've had with linux on iMac is to put fedora (20) on USB. Runs well but has radeon video driver issues.
It will boot OK and install - CAREFUL - it might also set itself to boot in preference to OSX.
To get OSX back you press Alt during boot and select Recovery image, then set Startup disk from Apple menu.

I think only fedora has a UEFI-boot-compatible image. (Maybe Archboot will do it too?).
I think this is probably a fail for linux packagers.
Windows is going exclusively UEFI-boot so recent PCs are set to UEFI mode in BIOS. 
Linux live DVDs should be set to UEFI boot, or at least have a UEFI boot version.
I note that clonezilla is now UEFI (and Secure boot) compatible, so it can be done.

---

### Post by wn1ytw on 2014-03-16
I have a mid-2011 12,1 that I can't use the dvd or usb media. My 'superdrive' is hosed so I have a samsung se-208ab/tsbs. I have burned 6 dvd's and all work on PC's but not my imac.  I have also burned several different usb sticks following  [http://www.ubuntu.com/download/desktop/burn-a-dvd-on-mac-osx](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-mac-osx) with no joy, I get errors saying &#8220;the disk you inserted was not readable buy this computer&#8221;.

The manual approach i get a message that the &#8216;drive&#8217; was not readable after step 9
but the resulting usb stick works on pc&#8217;s&#8230; so that manual approach does not work??


Both dvd and usb stick work on a pc but neither do any good things on my iMac &#8230; 


I have refind installed on the iMac I understand the usb not booting sort of, it is not &#8216;bootable&#8217; for mac? but I thought the dvd would work.

scott

EDIT:
 I'm using Mavericks OSX 10.9.2 
  Model Name:    iMac
  Model Identifier:    iMac12,1
  Processor Name:    Intel Core i5
  Processor Speed:    2.7 GHz
  Number of Processors:    1
  Total Number of Cores:    4
  L2 Cache (per Core):    256 KB
  L3 Cache:    6 MB
  Memory:    12 GB
  Boot ROM Version:    IM121.0047.B1E 

I made a little progress, I can get the machine to boot but with a black screen after "booting to blind mode". Try here: 
[http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/](http://www.makeuseof.com/tag/how-to-boot-a-linux-live-usb-stick-on-your-mac/)

scott
EDIT The external monitor did not help with my iMac-it is just stubborn.

---

### Post by entangled on 2014-03-18
I may have a partial answer to DVD not booting from internal drive...?
My iMac (21.5,mid-2010, version 11,2) would not recognize any DVD media in internal drive containing linux boot media. Now it does recognize some boot media.

I reset the PRAM, as advised by Apple when you get drive problems, but the difference is I did it several times.

You reboot the iMac and hold down cmd-Alt-P-R before the first chime. Keep the keys pressed and the iMac reboots twice more, chiming each time. The fourth and final reboot (and chime) happens after about another 2 mins wait. Release the keys and let the iMac boot normally. Mine took several minutes to get to desktop after this.
Results
Distribution     before PRAM reset                                                   after PRAM reset
Archboot         desktop reads DVD, DVD undetected at boot        desktop reads DVD, DVD boot succeeds
ubuntu 14.04  desktop rejects DVD as unreadable                        desktop fails to mount DVD, DVD detected at boot but 'No bootable device'
supergrub 2    desktop reads DVD, DVD boot fails                         desktop reads DVD, DVD detected at boot but 'No bootable device'
clonezilla         desktop reads DVD, DVD boots OK                         desktop reads DVD, DVD boots OK 
20140114

So Archboot DVD can now be booted (it wasn't possible before).
ubuntu 14.04 is accepted as readable on desktop, but not mountable or bootable, and supergrub2 can now be detected at boot time (but is not bootable).
This is better than before - just leaves the problem of most linux installers not being bootable on UEFI system. clonezilla seems to have solved this!

---

### Post by entangled on 2014-03-18
I see the spaces for my table are removed on posting:
Results[TABLE="width: 500"]
[TR]
[TD][B]distribution
[/B][/TD]
[TD]**before PRAM reset**[/TD]
[TD]**after PRAM reset** (4 times)
[/TD]
[/TR]
[TR]
[TD]Archboot[/TD]
[TD]desktop reads DVD, DVD undetected at boot[/TD]
[TD]desktop reads DVD, DVD boot succeeds
[/TD]
[/TR]
[TR]
[TD]ubuntu 14.04[/TD]
[TD] desktop rejects DVD as unreadable[/TD]
[TD] desktop fails to mount DVD, DVD detected at boot but 'No bootable device'[/TD]
[/TR]
[TR]
[TD]supergrub2[/TD]
[TD]desktop reads DVD, DVD undetected at boot[/TD]
[TD]desktop reads DVD, DVD detected at boot but 'No bootable device'[/TD]
[/TR]
[TR]
[TD]Clonezilla 20140114
[/TD]
[TD]desktop reads DVD, DVD boots OK[/TD]
[TD]desktop reads DVD, DVD boots OK[/TD]
[/TR]
[/TABLE]

---

### Post by wn1ytw on 2014-03-28
this is helpful also [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by panorain on 2014-03-31
I would like to ask if you are certain that you downloaded a PowerPC .iso. 

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Thanks,

---

### Post by wn1ytw on 2014-04-02
NO. I'm sorry, I was not and am not looking at the PowerPC at all, the new intel imac. Sorry for any confusion, I had hoped that link might be helpful but nothing specific.

---

### Post by mike4ubuntu on 2014-04-03
I just got this problem as well with the Saucy 13.10 Live USB on a SanDisk thumbdrive.  It gets to the purple screen, then BusyBox v1.20.2 with the (initramfs) error.  My system has a Gigabyte GA-970A-DS3P motherboard with a nvidia GEFORCE GT640 video card.  I've been able to use this same USB thumbdrive to boot/install on other systems with MSI motherboads.  It's just this Gigabyte motherboard that I have a problem with.  It's like the mobo's BIOS is ok with the SandDisk thumbdrive, because it actually gets to the thumbdrive to start the boot process.  But then once you get into the purple screen it loses access to the thumbdrive and doesn't see the initramfs anymore.  Anybody have a solution, or is this just a crappy motherboard?

---

