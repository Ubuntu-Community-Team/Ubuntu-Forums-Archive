---
title: "Installing Ubuntu on 2009 MacBook"
date: 2023-09-08
forum: Apple Hardware Users
---

### Post by merriww2 on 2023-09-08
I'm considering installing Ubuntu on my 2009 MacBook. The MacBook (6,1) is a late 2009 model with a 2.26 GHz Intel Core 2 Duo processor, 8GB DDR3 memory, NVIDIA GeForce 9400M 256 MB graphics processor, 500GB Solid State SATA drive with 260GB available space. I would like to dual boot and then ultimately remove the Apple OS.  Looking for advice on on what version Ubuntu and any thing to be aware of before I start the upgrade.

Thank you,
Wayne

---

### Post by yancek on 2023-09-08
You need to install a supported version for starters and that would be 20.04, 22.04 and 23.04.  Your hardware should be alright.  You might just download the latest Ubuntu release and test it by writing it properly to a usb.  If you have virtual software, you could just boot the iso using it.  If the latest Ubuntu gives you problems, you could try lighter versions such as Lubuntu, Xubuntu or Bodhi.

Nvidia can be problematic using Linux.  My understanding is that with every kernel update you need to reinstall the NVidia drivers.  Someone more familiar with NVidia may have more details.

I your MAC a UEFI or a Legacy install?  You need to install your Linux system in the same boot mode or it will not boot both on the same drive.

I'd suggest reading some documentation on installing Ubuntu, probably multiple sites to familiarize yourself with it before beginning.  The link below is the official Ubuntu Desktop Guide which gives a lot of information on what you can expect from Ubuntu.   Maybe read some sites on installing Ubuntu on a MAC, 2nd link below.  Also, use the Something Else or Manual option, whichever you have on your Ubuntu version.

[https://help.ubuntu.com/lts/ubuntu-help/index.html](https://help.ubuntu.com/lts/ubuntu-help/index.html)

[https://gist.github.com/cjonesy/2e2d8ca5e50ee1811f70](https://gist.github.com/cjonesy/2e2d8ca5e50ee1811f70)

---

### Post by merriww2 on 2023-09-08
Thank you for your advice. I'm going to do some more research and then proceed. Can't wait to try it out.

---

### Post by QIII on 2023-09-08
Moved to Apple Hardware Users for a more appropriate fit.

---

### Post by beameup on 2023-10-02
I've been playing with mine. 2009 15" Macbook Pro 5.4 Unibody. 8GB Ram 500GB SSD

Do live USB's first and try things out.

Wiped Snow Leopard out completely. No need for Refined or any of those.
Ubuntu 23.04 doesn't install the Broadcom wifi driver. You'll need to be on ethernet during install.
Enable it via Restricted Extras. Mine is the Broadcom BCM4322 (rev 1)
In my case, it still won't load the driver automatically. i have to do a modprobe command after reboot.
Even though it says it's enabled in Additional Drivers.
There is a sticky in the Networking forum. Best of luck to ya.

LMDE installed the driver by default. Maybe because of the older kernel. I'd have to try the LTS version of Ubuntu for comparison.
But when I installed it to the HDD, I had to do it over again. It stuck after that. Same with Fedora.

It doesn't install with Fedora, or Zorin. 
With Fedora you'll have to add the RPMFusion nonfree repo after install.
With Zorin you can add it from restricted extras and it will enable it before install.


Install TLP for power/battery help, and MBPFan to help with the fans.
Both of those run in the background. Just do an apt install.

Don't worry about Nvidia drivers. Use the stock opensource driver that installs by default..

Battery is about 5 years old. I get an hour, and it drops off and dies quickly.


Update: I installed Ubuntu LTS on it today. Let me load the wifi driver without hooking up ethernet.
But after installation, I had to hook up an ethernet to enable it. It stays loaded after a reboot, so I'd definitely say the newer kernels may have a bug.

---

### Post by CoopOne on 2023-11-24
I tried to install Ubuntu 22.04 on my 2009 15" Macbook Pro 5.4. Unfortunately, the keys for screen brightness didn`t work under nouveau driver even when if I logged to X.org (instead of Wayland). I tried to install legacy nvidia-340 driver for GeForce 9400M, but with no success.

Finally, I installed MX Linux 23 and used Nvidia Driver Installation tool to compile nicely legacy nvidia-340 driver under the newest kernel version 6.1. The keys for screen brightness adjusting started to work ;) 

I also downloaded firmware for Apple iSight camera from that [LINK]("https://www.linux.org/attachments/appleusbvideosupport-zip.4683/") and installed isight-firmware-tools. You have to switch off and switch on the notebook after applying the firmware (restart is not enough).

---

