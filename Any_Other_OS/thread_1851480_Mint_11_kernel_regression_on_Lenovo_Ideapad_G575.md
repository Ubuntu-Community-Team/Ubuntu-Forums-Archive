---
title: "Mint 11 kernel regression on Lenovo Ideapad G575"
date: 2011-09-22
forum: Any Other OS
---

### Post by Juraj Cerven on 2011-09-22
I have recently (in august 2011) purchased notebook **Lenovo IdeaPad G575** AMD Fusion without OS

Processor: AMD Zacate Dual-Core E-350 1,6 GHz, 2x 512 KB L2 Cache 2 core, max TDP: 18 W
RAM: 1x 2 GB DDR3 1066 MHz
Display: 15,6" LCD TFT LED illumination glossy, resolution 1366 x 768
Graphics card (internal in processor chip): AMD Radeon HD6310
HDD: 320 GB 5400 RPM
DVD: SuperMulti DVD-RW DL
Integrated sound card
Stereo spekers
Webcam

Ethernet 10/100 Mbit/s
Wireless LAN 802.11b/g/n
4x USB 2.0
1x D-Sub (VGA)
1x RJ-45
1x Mic
1x Headphones
1x card reader 2in1 (SD/ MMC)

This model is quite new (2011) so I would understand, that it won't work with older versions of Linux. But opposite has happend.

I tried to boot live DVD Linux Mint 11 Katya 64 bit.
System started booting, but as it came to start GUI **it has frozen** and only hard reset has helped.

Later I have tried to boot Linux Mint Debian Gnome 2011-08 64 bit live DVD and Kubuntu 11.04 64 bit live CD (I wanted to verify if the problem could be in Gnome) with the same sad result.

Ubuntu 11.10 Beta1 failed to boot too. Both 64 bit and 32 bit versions. The system has always frozen at some point.

I have always checked md5sum for iso image and also md5sum -c md5sum.txt for burned DVD. Everyting was OK.

I have tried various boot option combinations (nomodeset acpióff pci=routeirq ...) and BIOS sata mode = AHCI - all sugested in various Linux forums, but nothong has helped.

Also starting Mint in Compatibility Mode didn't helped. Mint Debian was able to run in terminal mode, but has reported "Boot failed".

All these media booted with no problem on my desktop PC.

I would be sure that problem was in hardware, but to my surprise **Ubuntu 10.10 Maverick 32 bit and Linux Mint 10 Julia (both 64 and 32 bit) booted from live CD/DVD with no problems**.

I have finally installed Linux Mint 10 64 bit, and everythig workes fine.
Just graphics has had resolution 1024 * 768 immediately after installation.
When I have installed additonal drivers from Mint repository I have got resolution 1366 * 768 but "AMD unsupported hardware" watermark appeared in the right lower corner of the screen.
Later I have replaced fglrx version 2.8.780 (from repository) with newer version fglrx_8.881-0ubuntu1_amd64.deb from AMD web site and everything workes perfect with no watermark.

To verify hypothesis that problem is in kernel I have tried Fedora 15 live CD - computer has frozen.
Fedora 14 live CD works fine :-)

So it looks like **kernel 2.6.35 works fine, higher kernel freezes**.

So I am very dissapointed with this **FATAL REGRESSION**. I hope that till new version of Mint 12 or Ubuntu 11.10 this problem will be solved, as I don't want to stick to Mint 10 forever.

This type of regression is great shame for Linux which **can discourage many potential users from using Linux**. I would like to recommend Linux (Ubuntu or Mint) to my friends, but in this situation I cannot.

Please, help me to fix this problem.

---

### Post by Juraj Cerven on 2011-09-28
To be more precise, I have reported here, because the problem is not only in Linux Mint, but also in Ubuntu and other distribution of Linux. I don't know where is the proper place where I should report it.

Plese help to forward this problem to people who can correct kernel.

---

### Post by Perfect Storm on 2011-09-28
Moved to Other OS/Distro Talk.

---

### Post by el_koraco on 2011-09-28
It's probably not the kernel, but the fresh version of X in Fedora and Ubuntu plus the open source drivers. It would most certainly work right with AMD's driver. Try to boot the Live CD with adding nomodeset to the kernel line, that should get you to a rudimentary desktop.

---

### Post by freechelmi on 2011-10-03
> **el_koraco said:**
> It's probably not the kernel, but the fresh version of X in Fedora and Ubuntu plus the open source drivers. It would most certainly work right with AMD's driver. Try to boot the Live CD with adding nomodeset to the kernel line, that should get you to a rudimentary desktop.

Nope, Same here even with NoModeSet , freeze after the Drm loading it seems.

Apart from installing from the alternate CD in texte mode and install the AMD drivers manually I don't really see a solution

---

### Post by freechelmi on 2011-10-07
We should also check this bug : 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034)

---

### Post by freechelmi on 2011-10-08
Ok Got it working now : 

- installed with AlternateCD (not sure the issue cas related to amd drivers then)

- Add "blacklist atl1c"  in /etc/modprobe.d/blacklist.conf

- Call update-initramfs -u  to update the modules loaded at boot.


No more freeze, but no more ethernet obviously.

---

### Post by Juraj Cerven on 2011-10-08
> **freechelmi said:**
> Ok Got it working now : 

- installed with AlternateCD (not sure the issue cas related to amd drivers then)

- Add "blacklist atl1c"  in /etc/modprobe.d/blacklist.conf

- Call update-initramfs -u  to update the modules loaded at boot.


No more freeze, but no more ethernet obviously.

Thanks a lot, for me is this workaround satisfying:

- ethernet plugged
- Wifi disabled ( via hardware button ) 
- Boot and install LinuxMint11 from LiveDVD
- Add "blacklist atl1c" in /etc/modprobe.d/blacklist.conf
- Call update-initramfs -u to update the modules loaded at boot.

No more freeze, but no more ethernet obviously. It is no problem since WiFi works OK.
No problem with AMD graphics driver, installed from repository, everything works well.

Card reader repaired according to:

[http://ubuntuforums.org/showthread.php?p=11316191#post11316191](http://ubuntuforums.org/showthread.php?p=11316191#post11316191)

Now I am happy with this status :D. All hardware except ethernet works now perfect.

---

### Post by freechelmi on 2011-10-10
> **Juraj Cerven said:**
> Thanks a lot, for me is this workaround satisfying:


Apart from that , do you confirm that the Fan is really loud all the time ?

---

### Post by Juraj Cerven on 2011-10-10
> **freechelmi said:**
> Apart from that , do you confirm that the Fan is really loud all the time ?

I don't think it is too loud.

For complete list of used workarounds I add this:

This notebook also freezes when connecting to WiFi on battery power. I am using the temporary work around from [http://www.uluga.ubuntuforums.org/showthread.php?p=10327529](http://www.uluga.ubuntuforums.org/showthread.php?p=10327529) : "sudo iwconfig wlan0 power off" before trying to connect to wlan when running on battery.

(from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/684164](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/684164) comment #9)

---

### Post by freechelmi on 2011-10-15
Hi good news on my side : 

- the trick for Aspireone 522 seems to work : Putting the network card first in boot order and the kernel freeze dos not occur with either eth plugged or not and wifi activated or not.


- I don't have the same issue as you : connecting to wifi on battery does not freeze the machine.

the last problem, I have to do a "rfkill unblock all" on Live CD to make the wifi working

---

### Post by Juraj Cerven on 2011-10-29
It's a kind of magic :)
I have tried it with Linux Mint 11 Live DVD.
It works perfect.

The issue with wifi freeze on batery was probably only on Mint 10 (based on Ubuntu Maverick).

---

### Post by novikov on 2011-10-31
method from freechelmi works. (I did so a couple of weeks already):

reboot 
enter the bios 
set "network boot" to first option 
save and reboot again. Now your system won't freeze. 

this seems dirty, but worked for me (lenovo g575, ubuntu 11)

---

### Post by Juraj Cerven on 2011-12-09
Hi. I have new information.
I have recently switched to Linux Mint 12 (based on Ubuntu 11.10).

Unfortunately, the trick with changed BIOS boot order didn't work anymore with this release.

Fortunately this solution works further:
- Add "blacklist atl1c" in /etc/modprobe.d/blacklist.conf
- Call update-initramfs -u to update the modules loaded at boot.

---

### Post by Juraj Cerven on 2012-05-22
Hi,

I have tried Linux Mint 13 RC and I hoped that the problem with Lenovo Ideapad G575 was already solved (now that hardware is not so new).

But the system freezes again.
Even workaround which has helped with Mint 11 and 12 did not helped:

- ethernet plugged
- Wifi disabled ( via hardware button ) 

I was not able to boot from live DVD. The system freezes after some minutes. Can anybody help?

Thanks Juraj

---

### Post by Juraj Cerven on 2012-05-23
Aplogise for false alarm. Trick with ethernet plugged works, I had connect wrong cable.

> **Juraj Cerven said:**
> Hi,

I have tried Linux Mint 13 RC and I hoped that the problem with Lenovo Ideapad G575 was already solved (now that hardware is not so new).

But the system freezes again.
Even workaround which has helped with Mint 11 and 12 did not helped:

- ethernet plugged
- Wifi disabled ( via hardware button ) 

I was not able to boot from live DVD. The system freezes after some minutes. Can anybody help?

Thanks Juraj

---

### Post by freechelmi on 2012-09-25
I confirm the problem is still here with the 12.04 kernel and that the "Netwok Boot first" solve the problem

---

### Post by Juraj Cerven on 2012-11-30
Hi all,

I have recently upgraded to Linux Mint 14 (based od Ubuntu 12.10) and the problem is there solved. Boot from live DVD works without problems.

---

