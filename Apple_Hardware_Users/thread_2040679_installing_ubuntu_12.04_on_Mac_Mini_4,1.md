---
title: "installing ubuntu 12.04 on Mac Mini 4,1"
date: 2012-08-11
forum: Apple Hardware Users
---

### Post by janod on 2012-08-11
Hello,

I am trying to install Ubuntu 12.04 on MacMini 4,1 (model with Nvidia graphic chipset) from an USB drive. When I select "Try Ubuntu Without Installing", the OS will boot but end up in strange graphic mode with strips over the upper part of the screen.

I managed to install 10.10 by setting boot parameters to  "**nomodeset reboot=pci"** but this doesn't work with 12.04 anymore.

I went through several posts and have tried various options e.g. "**nomodeset xforcevesa"** or **"blacklist=vga16fb"** with no luck. Adding the "nomodeset" option makes the starting screen to show up but then it switches to a text console.

Any hints appreciated.

Regards,
Jan

---

### Post by davidryderuk on 2012-08-12
Hi,
Since your computer has the same graphics card as the Macbook Air 3,2, this might be relavent:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/898784)

In that case the issue was solved by updating to Ubuntu Kernel version 3.2.0-27.

---

### Post by janod on 2012-08-14
Hello,

Thanks for an advice. Which ISO image has the kernel version 3.2.0-27 ?
Should I go for [http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso) which is adjusted for Macs and might have the fixed kernel or shall I go for the latest daily build of 12.10 which should have the fixed kernel ?

Thanks,
Jan

---

### Post by davidryderuk on 2012-08-14
I don't think any of the Ubuntu 12.04 iso images will have kernel version 3.2.0-27. They don't tend to get updated between releases. You might get the latest kernel if you install Ubuntu 11.10 and then upgrade to Ubuntu 12.04. 

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

The amd64+mac.iso is worth a try, though if it works it won't be because of an updated kernel. The main difference is that the amd64+mac.iso boots in Bios Compatibility Mode, instead of UEFI mode. 

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Ubuntu 12.10 is still in alpha, so I wouldn't use it for anything important. It will have a lot of new, untested packages.

---

### Post by janod on 2012-08-14
Hello,

Thanks for your hints. I will try different ISOs and post the results.

Jan

---

### Post by davidryderuk on 2012-08-15
The Ubuntu 12.04.1 release should have a more recent version of the 2.6.0-x kernel. According to Zdnet it will be released in a few days. Perhaps you could try it when it's released.

[http://www.zdnet.com/ubuntu-12-04-1-lts-maintenance-release-7000002616/](http://www.zdnet.com/ubuntu-12-04-1-lts-maintenance-release-7000002616/)

---

### Post by janod on 2012-08-15
Thanks for this tip! I'll give it a try and report back.

---

### Post by janod on 2012-08-29
Hello,

I tried to boot 12.04.1 amd64 version from an USB stick (EFI booting), and again end up with a scrambled desktop. I tried then "nomodeset" option which boots fine for a short while and then ends up in a command prompt.

I did "dmesg | tail" and here are last few lines:
```

init: lightdm main process (1833) terminated with status 1
....
init: plymounth-stop pre-start process (2652) terminated with status 1
....
init: failsafe-x main process (2529) terminated with status 1

```I then checked /var/log/Xorg.0.log and Xorg.failsafe.log and here are some lines:
```

(EE) [drm] failed to open device

LoadModule: "VESA"
Loading submodule "vbe"
Loading submodule "int10"

(EE) VESA(0): V_BIOS address 0xd00 out of range
(EE) Screen(s) found, but none have a usable configuration

```Any hints how to move forward are highly appreciated.

Thanks,
Jan

p.s. I also tried 12.04.1 amd64+mac - this iso however boots in BIOS compatible mode only and won't boot from an USB

---

### Post by davidryderuk on 2012-08-30
I haven't any real ideas, sorry. 


Maybe you could look at nouveau's troubleshooting pages:
nouveau.freedesktop.org/wiki/KernelModeSetting
nouveau.freedesktop.org/wiki/TroubleShooting

Or alternatively you could use virtualisation, an older version of Ubuntu, or try another distro (like Fedora). 

[http://osxdaily.com/2012/03/27/install-run-ubuntu-linux-virtualbox/](http://osxdaily.com/2012/03/27/install-run-ubuntu-linux-virtualbox/)

---

### Post by jasunto on 2012-08-31
i am going to be trying to install ubuntu server on my mac mini 4,1 server with dual hard drives and no optical, since i just need the server and no GUI and just a wired connection, do you think it will work fine? I may also try alternate installer and make a raid 1 out of my two mac mini server disks.

---

### Post by janod on 2012-09-03
Hello,

Good news. On Macs and some new PCs, one can boot either in EFI mode (EFI being new replacement of legacy BIOS) or in legacy BIOS mode. I found out that if I boot from an USB I can only boot in EFI mode. Booting in EFI mode is known to have issues with certain linux video drivers - in particular nVidia chipsets don't work well when booting in EFI.
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

I therefore burned a CD with 12.04.1 amd64 and booted it in BIOS compatibility mode ([http://dustin.li/2011/05/how-to-install-ubuntu-11-04-on-a-mac-mini/](http://dustin.li/2011/05/how-to-install-ubuntu-11-04-on-a-mac-mini/)). This worked well and I could boot 12.04.1 all the way into the Unity desktop.

BIOS compatibility mode offers good graphics performance so I'll stick with it and try to proceed with fresh install. Let you know how it goes.

---

### Post by davidryderuk on 2012-09-03
Thats good news. 

Good luck with the fresh install.

---

### Post by Goyakla on 2012-09-04
I'm late, I read only now your commentaries. But I hope that my observations will be read. I have a **mac mini mid 2012, with a CPU P8800 and a graphic card nvidia geforce 320M**. I used on it the Ubuntu 10.10, with the proprietary driver nvidia, which run very well in bios emulation mode.
 Recently I've installed the 12.04 version. To do it, I used the alternate distribution and installed it in the bios emulation mode. After the installation I passed to the kernel, on the command line, “nomodeset reboot=noacpi”, because it was impossible to use the driver “nouveau”. It seems that it's incapable to recognize the graphic card.
 It's strange because this driver with the 12.04 run very well on the macbook pro 7.1, which has the same processor and above all the same graphic chip (nvidia geforce 320M). And not only in bios emulation mode but in **EFI mode**, that is the mode I use with the macbook pro.
 In the mac mini, xorg was using the vesa driver, which is limited in the dimension of the display, 1024x768, I believe. So it's for this reason that we were obliged to add the nomodeset option.
 After to upgrade Ubuntu, I added temporally the repository proposed and install the proprietary driver nvidia 304.43. The result is good but the display is not so good as with Ubuntu 10.10 which is very excellent as the one I obtained on the macbook pro with the 12.04 version with the driver nouveau in EFI mode. I don't know why !
 May be it's possible to oblige the driver “nouveau” to recognize the graphic card to pass to it some parameters ? Somebody has any idea ?
 I will look for more information and in any way I will try with the 12.10 distribution. But it's a petty because the 12.04 is one of the best Ubuntu distribution. I will continue to report my experience if any body is interesting. :p

---

### Post by janod on 2012-09-17
Hi,

Thanks for sharing your experience on nvidia drivers. If you get any further on MacMini please let us know. I want to use Ubuntu also for photography processing.

Jan

p.s. I haven't have time to install 12.04 on MacMini (in BIOS compatible mode) yet but I'll report back when I do.

---

### Post by janod on 2012-11-27
Hello,

I managed to successfully instal Ubuntu 12.04.1 on my Mac Mini 4,1. I did the triple boot scenario with MacOS, Ubuntu and Win7.

0) MacOS X was already installed
1) I created a custom GPT partition layout for Ubuntu and Win7 (in Ubuntu I wanted to have separate backup partition etc.). I did it by booting Ubuntu CD and creating partitions from within the temporarily booted Ubuntu.
2) I hybridized main partitions into a hybrid MBR from within MacOS using gdisk.
3) I installed rEFIt from within MacOS.
4) Then I was ready to proceed with an installation of Win7.
5) And finally, I installed Ubuntu. The trick here was to boot Ubuntu from a CDROM in BIOS mode (holding C while booting). Boot loader (grub) has to be installed in / partition or other dedicated partition, not in MBR).

The point is that Win7 partition and Ubuntu partition with Grub must be included in hybrid MBR. Once Ubuntu is booted it can "see" an entire GPT table.

I found the following links helpful.
[https://help.ubuntu.com/community/MacBook/TripleBoot](https://help.ubuntu.com/community/MacBook/TripleBoot)
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

Cheers,
Jan

---

### Post by tiverson-t on 2013-10-02
FYI for others that find this useful thread:  I was having horrible graphics problems (screen flashing on and off) and these were resolved by switching from the minidvi-to-vga cable to the hdmi-to-dvi cable.  Also, 12.04.3 is too large for a CD, but I was able to find and download 12.04.2, which is JUST less than 700MB.

---

