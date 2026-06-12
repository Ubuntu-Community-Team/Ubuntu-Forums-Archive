---
title: "Wirless adapter not working"
date: 2020-04-07
forum: Apple Hardware Users
---

### Post by elopezavila on 2020-04-07
Hello,

I've recently installed 18.04 in a old MAC desktop. The installation went smoothly and everything is working but the wireless adapter.

I cannot plug in a RJ45 cable to it so I'm using another computer to download the drivers.

Steps that I went through:
-Copied the OS ISO to ubuntu, mounted and tried to install the driver......failed
-Found that the adapter is: BCM4322 and followed some instructions on getting [the drivers here]("https://packages.ubuntu.com/bionic/firmware-b43-installer"), included the b43 fwcutter which the installation said was required.

But once the B43 firmware is installing, it states the following:
```

No chroot environment found. Starting normal installation
--2020-04-07 07:38:58-- http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com... failed: Name or service not known.
wget: unable to resolve host address 'www.lwfinger.com'
Some problem occurred during the firmware download. Please check your internet connection.

```

I downloaded this file and tried to install it, but then it states that the file is not **Debian format archive. **I've extracted its content but then, I have no idea where to put those files.

Any idea on how to solve this?

Thank you.

---

### Post by chili555 on 2020-04-07
> 
I've extracted its content but then, I have no idea where to put those files.
What are the files? What are the names of the first several? Are they all in .fw format? Something like this?

```
a0g0bsinitvals5.fw		lcn400initvals33.fw    sslpn1bsinitvals27.fw
a0g0bsinitvals9.fw		lp0bsinitvals13.fw     sslpn1initvals20.fw
a0g0initvals5.fw		lp0bsinitvals14.fw     sslpn1initvals27.fw
a0g0initvals9.fw
```

---

### Post by slickymaster on 2020-04-07
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by elopezavila on 2020-04-07
The files are the following:

```

/config/
wl.mk
wlconfig_lx_shared
wlconfig_nomimo
wl_default
wl_hnd
/linux/
wl_ap.o
wl_apsta.o
wl_sta.o

```

And a README.txt file:
```

This driver was extracted out of the GPL source package for NETGEAR WNDR4500

It contains the Broadcom wireless driver 5.100.138
This driver includes firmware version 666.2

http://www.downloads.netgear.com/files/GPL/WNDR4500-V1.0.0.40_1.0.10_src.tar.zip
WNDR4500-V1.0.0.40_1.0.10_src/src/wl

```

That's it.

Thank you!

---

### Post by gsahli on 2020-04-07
Keep working at it:
[https://ubuntu-mate.community/t/how-to-get-and-install-the-broadcom-wifi-driver-for-version-18-04/17304](https://ubuntu-mate.community/t/how-to-get-and-install-the-broadcom-wifi-driver-for-version-18-04/17304)
[https://askubuntu.com/questions/1105857/install-broadcom-wireless-drivers-on-ubuntu-18-10-without-internet](https://askubuntu.com/questions/1105857/install-broadcom-wireless-drivers-on-ubuntu-18-10-without-internet)
[https://noobsplanet.com/index.php?threads/install-bcm-43xx-wireless-card-driver-in-ubuntu.22/](https://noobsplanet.com/index.php?threads/install-bcm-43xx-wireless-card-driver-in-ubuntu.22/)

---

### Post by chili555 on 2020-04-08
Please see post #11 here: [https://ubuntuforums.org/showthread.php?t=2361632&highlight=b43.zip](https://ubuntuforums.org/showthread.php?t=2361632&highlight=b43.zip)

---

### Post by chili555 on 2020-04-08
> **gsahli said:**
> Keep working at it:
[https://ubuntu-mate.community/t/how-to-get-and-install-the-broadcom-wifi-driver-for-version-18-04/17304](https://ubuntu-mate.community/t/how-to-get-and-install-the-broadcom-wifi-driver-for-version-18-04/17304)
[https://askubuntu.com/questions/1105857/install-broadcom-wireless-drivers-on-ubuntu-18-10-without-internet](https://askubuntu.com/questions/1105857/install-broadcom-wireless-drivers-on-ubuntu-18-10-without-internet)
[https://noobsplanet.com/index.php?threads/install-bcm-43xx-wireless-card-driver-in-ubuntu.22/](https://noobsplanet.com/index.php?threads/install-bcm-43xx-wireless-card-driver-in-ubuntu.22/)

I believe that all of these posts describe installation of bcmwl-kernel-source. That is not the appropriate driver for his device.

---

### Post by gsahli on 2020-04-08
> **chili555 said:**
> I believe that all of these posts describe installation of bcmwl-kernel-source. That is not the appropriate driver for his device.

No, sorry. It may be called "source" but it is firmware. The Broadcom chipset requires that the firmware be installed to the chip on every startup. wildmanne39 explained that in the post you linked.

---

### Post by chili555 on 2020-04-09
> **gsahli said:**
> No, sorry. It may be called "source" but it is firmware. The Broadcom chipset requires that the firmware be installed to the chip on every startup. wildmanne39 explained that in the post you linked.I am very familiar with the drivers for Broadcom devices. There are four possible drivers for Broadcom devices: b43/bcma and firmware; bcmwl-kernel-source, brcmsmac and  brcmfmac and different firmware. 

Not every driver works well for every device and, in most cases, doesn't work at all.

bcmwl-kernel-source provides the driver *wl*, not just firmware, which is wrong for his 4322 device. He needs and is trying to install the .fw files needed to utilize the b43/bcma and firmware driver suite.

I suggest that you check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) and here: [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers/60395#60395](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers/60395#60395)

---

