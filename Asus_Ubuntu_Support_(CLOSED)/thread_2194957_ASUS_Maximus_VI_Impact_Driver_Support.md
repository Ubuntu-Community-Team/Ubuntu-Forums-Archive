---
title: "ASUS Maximus VI Impact Driver Support"
date: 2013-12-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by matthew.hegedus on 2013-12-21
I'm having major headaches getting this board set up with Ubuntu 12.04 LTS.

My current kernel version is 3.2.0-57-generic and it's a 32-bit install.

Intel Ethernet Controller: On initial boot linux did not recognize any devices. I googled and actually had some success with this yesterday. I shuttled various packages between my networked windows box and this Maximus IV linux build in preparation of trying to build Intel's e1000e kernel module which I downloaded from their website. I ran through their simple build steps and linux recognized the onboard ethernet and I was able to browse from linux. I decided to run the ubuntu software updater which required a reboot. After the reboot, I was updated to 3.2.0-56-generic from 3.2.0-57-generic and it appears the updater undid my previous work as no ethernet device is acknowledged. Of course if I try to rebuild and reinstall the intel e1000e module the build complains that it cannot find the correct dependencies. Sigh - I will try to shuttle the proper packages from my windows box again.

Broadcom WIFI: No go yesterday. I tried to build and install various kernel modules, including one from Broadcom that claimed it supported BCM4352 (I ran 'lspci' to get that info). Linux would not recognize this hardware.

Logitech K800 wireless keyboard: This worked great out of the box on my old hardware with Ubuntu 12.04 LTS. It also works great when I boot to the BIOS on the Maximus VI Impact. It does not work when Ubuntu 12.04 LTS boots with this mobo. Preliminary googling suggests everyone thinks this should work out of the box, and I don't see any links to try to manually install any drivers.

The onboard bluetooth receiver is not recognized either. I have yet to dig into this ... it's the lowest of my priorities.

If anyone else out there has similar issues, please confirm and maybe we can help each other. I will try to post again if I figure anything out.

And of course, if you know how to resolve these issues please let me know.

---

### Post by matthew.hegedus on 2013-12-21
Ok, I knew I should be able to at least get the ethernet working again... I finally did. Even though my kernel version 3.2.0-57-generic (use 'uname -r' to get that info) , I hardcoded intel's Makefile to include 3.2.0-58-generic headers. Specifically, I added this line in the assignment of the KSP Makefile variable:

/usr/src/linux-headers-3.2.0-58-generic

That allows it to build the module again (I probably didn't need to build it again). I am grateful the Makefile is verbose when you run 'make install' because it shows exactly what commands it is using. It wants to install the kernel object in 3.2.0-58-generic module directory, but I want it to install in the 3.2.0-57-generic module directory. So I just hand modified the commands and ran then from the command line ...

install - D -m 644 e1000e.ko /lib/modules/3.2.0-57-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
/sbin/depmod -a || true
rmmod e1000e; modprobe e1000e

That was enough to get the onboard ethernet recognized. I apologize if I made any typos or mistakes. Also, I won't claim that these manual steps are the correct way to proceed. I'm not a low-level linux expert. I'll continue looking to see if I can get that Logitech keyboard working. I dunno how quick the Ubuntu community is in updating ubuntu to support these things on this mobo, but hopefully it is sooner than later so people wont have to mess with these involved and error prone processes.

---

### Post by matthew.hegedus on 2013-12-21
Ok, the Logitech K800 keyboard is now working ... I came across some documentation on Logitech's website indicating issues when using multiple receivers with some in usb 2.0 ports and others in usb 3.0 ports. For some reason that configuration causes interference  issues.

I figured my ASUS Maximus VI Impact only had usb 3.0 but it has a mix of 2.0 and 3.0 ports. I plugged my two wireless input device usb receivers in the usb 2.0 ports and both work as expected. Strange.

---

### Post by roby-programmer on 2013-12-29
hi
I am planing to buy this motherboard and put on ubuntu 14.04, I would like to know what is working and what not

For example, did you have any problem with soundcard?

Can i ak you to put here the result of [COLOR=#000000][FONT=Times New Roman]lspci -n?

Abou wireless and bluyethoot I see the [/FONT][/COLOR][COLOR=#000000]bcmwl-kernel-source package is updated with the suppport to broadcome 4352 only in ubuntu 14.04, and that driver if I am not in wrong require 3.8 kernel

thank you bye[/COLOR]

---

### Post by NcA on 2014-01-01
Matthew, have a look at installing [Solaar](https://launchpad.net/~daniel.pavel/+archive/solaar) to help with your Logitech issues.

I'm also curious about this board, especially the add-on audio card support.

---

