---
title: "nVidia drivers"
date: 2012-07-28
forum: Apple Hardware Users
---

### Post by timbim on 2012-07-28
Hi,

I've just installed 12.04 on a clean SSD in my 7.1 13" MBP.  I was looking at [this guide]("https://help.ubuntu.com/community/MacBookPro7-1/Oneiric#Video"), and followed the instructions in the video section.  On rebooting, I get to an ubuntu splash, the display then goes black and doesn't respond at all.  The nVidia drivers installation was the only thing I did in the boot prior to the problem arising.

Any ideas what's going on and how I can fix it, or am I going to have to reinstall?

---

### Post by timbim on 2012-07-28
I've also tried another couple of approaches as suggested [here]("http://yoodey.com/full-installation-ubuntu-precise-pangolin-1204-macbook-pro-71") and similarly [here]("http://yoodey.com/solve-macbook-pro-71-vga-nvidia-black-screen-not-detected-external-display-doesnt-work-ubuntu") but both of these lead to the same black screen and no activity after the ubuntu splash screen after booting.

Am I just going to have to live with the generic graphics drivers or is there some other method I'm unaware of?

---

### Post by firekage on 2012-07-28
As a matter of fact, installing all kind of nvidia drivers from their web or from x-swat and the other in my case crashed my X on my desktop machine. The only driver that worked for me was the one from Ubuntu repos (from install CD). As soon as i installed x-swat or nvidia binary than either i couldn't get past splash screen cause X stopped working and i had to switch to terminal, kill X and try again, or if i succeded entering GUI after splash screen than anything what i did caused to freezed X so...again had to kill X, enter terminal and so on...i had enough it and stick with the driver from install cd /ubuntu repo.

Still don't know why only one worked for 11.10.  The same thing happened with 12.04...

---

### Post by davidryderuk on 2012-07-29
Hi,
I have the Macbook 7,1. I've found that:

The Nvidia drivers fail to work when booting in EFI mode and result with, like you describe, a blank screen. 

The Nvidia drivers work when booting in BIOS Compatibility mode, however then the HD/SSD drivers only support IDE compatibility mode. 

If you want to install Ubuntu in BIOS Compatibility mode, then burn Ubuntu to CD, hold down the Option key and select "Windows Disc" (or similar). 

Good luck.

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://bugzilla.kernel.org/show_bug.cgi?id=15923](https://bugzilla.kernel.org/show_bug.cgi?id=15923)

---

### Post by davidryderuk on 2012-07-29
p.s. Did you try the 'amd64+mac.iso'? That CD only boots in BIOS compatibility mode, so I would have expected it to work.

---

### Post by timbim on 2012-07-29
I did try the mac iso, it wouldn't boot off the USB I made from it, so I just kept going with the standard 64 bit CD, which did work.  I could burn it, and I might try later on once I've got an image of the working OS I've got at the moment.

If I use a BIOS booting method and therefore IDE mode on the SATA controller, that will nail my SSD performance won't it?  Will the kernel fix mentioned [here]("https://bugs.launchpad.net/mactel-support/+bug/817017") fix that or not?

---

### Post by davidryderuk on 2012-07-29
I know that Macs don't generally boot Ubuntu off USB when booting in BIOS Compatibility mode. Booting from a CD should work, but I have had problems in the past.

I don't have an SSD drive, just the HD the computer came with. I imagine it would be slower though. 

I found the "setpci -d ****:**** **.*=**" command last month. I spent a long time trying to find the right bits to change on the register. I only got as far as reproducing the error mentioned in this bug report:

[https://bugzilla.kernel.org/show_bug.cgi?id=15923](https://bugzilla.kernel.org/show_bug.cgi?id=15923)

If you manage to switch the SATA controller into AHCI mode please post. I found the same command mentioned here, if its of any interest:

[http://www.insanelymac.com/forum/index.php?showtopic=126089&st=0](http://www.insanelymac.com/forum/index.php?showtopic=126089&st=0)

---

### Post by milan475 on 2012-12-11
I just filed a bug about this problem: [https://bugs.launchpad.net/ubuntu/+bug/1088963](https://bugs.launchpad.net/ubuntu/+bug/1088963)

---

