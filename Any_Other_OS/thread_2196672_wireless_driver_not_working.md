---
title: "wireless driver not working"
date: 2013-12-30
forum: Any Other OS
---

### Post by delgado1kevin on 2013-12-30
Hey guys, new to linux here. Just installed Linux Mint 16 today. When I was trying it with the LiveUSB every time it would boot I would be disconnected from the internet, would install the bcmwl-kernel-source and it would work fine. Now that I have installed it, when I go to install the driver I get thrown the error:

The package 'bcmwl-kernel-source' could not be installed
please check your connection to the internet.

When I open up driver manager i see:

Broadcom Corporation: BCM4331 802.11a/b/g/n
This device is not working.

(followed by two radio buttons)
-bcmwl-kernel-source
Version 6.30.223.141+bdcom-0ubuntu1
Broadcom 802.11 Linux STA wireless driver source

-Do not use the device

The "do not use the device" one is checked and when i check the other one and hit apply changes it automatically goes back to the "do not use the device"

Any help?

---

### Post by oldos2er on 2013-12-30
Moved to Other OS/Distro Support.

---

### Post by varunendra on 2014-01-04
Welcome to Ubuntu Forums delgado1kevin !

Please try this -
```
sudo apt-get purge bcmwl-kernel-source
```
..to remove the sta driver and its configuration files. We'll be trying the native driver "b43" now.

While being connected to internet via cable or other means, please install the firmware package which contains the firmware required by the native driver -
```
sudo apt-get install linux-firmware-nonfree
```

If you have no way to connect Ubuntu to internet, manually download the above package from here : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

Copy the downloaded .deb file to your desktop, and install it with double-click, or -
```
sudo dpkg -i Desktop/linux-firmware-nonfree_1.14ubuntu1_all.deb
```

Reboot and let us know if you have your wifi back. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

