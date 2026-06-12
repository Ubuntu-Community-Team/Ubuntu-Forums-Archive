---
title: "[SOLVED] Ubuntu Wireless internet"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by jediryan123 on 2007-12-13
Hi I just bought a belkin f5d7050 wireless internet usb thing off the internet it should be here in a few days is there anything I have to install or code to type in to get it to work I am running ubuntu 7.10 and I don't know much code.

cheers

---

### Post by d0nny2600 on 2007-12-13
There is a community dedicated to writing a driver for that particual interface. It can be found here

[http://zd1211.ath.cx/](http://zd1211.ath.cx/)

Thats the best info I can give you

---

### Post by jediryan123 on 2007-12-13
Thx Donny should this driver be pre intalled on ubuntu?

---

### Post by d0nny2600 on 2007-12-13
Im not too sure if its preinstalled. You can download it from that link and follow their instructions. Should sort you out!

---

### Post by jediryan123 on 2007-12-13
Thanks Donny appreciate the help.

---

### Post by superm1 on 2007-12-20
That driver does appear to be shipped in gutsy.  I'm not sure on the firmware though:

```
supermario@portablemario:/lib/modules/2.6.22-14-generic$ find ./ -name zd1211rw*./kernel/drivers/net/wireless/zd1211rw
./kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
```

---

### Post by Chadarius on 2007-12-28
This card is supported in 7.10 out of the box. However, if you need it to connect to WPA encrypted wireless networks you will need to update the firmware. This is really easy.

Newer versions of the Linux kernel (kernel 2.6.18-rc1 and higher) already contain the latest zd1211rw drivers. You do not need to blacklist or compile any drivers. In fact, if you are using unencrypted or wep encryption you should have full support built directly into the 7.10 release. However, WPA is not supported without updating the firmware for this usb wireless card.
Updating the firmware to support WPA

[LIST=1]
[*]Download the firmware
[INDENT]Download zd1211-firmware-1.4.tar.bz2 from [http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083)[/INDENT]
[*]Uncompress and untar the file with the following command (or your favorite way to handle tar.bz2 files
[INDENT]```
tar -xvvjf zd1211-firmware-1.4.tar.bz2
```[/INDENT]
[*]Copy the firmware files to the proper location
[INDENT]```
cd zd1211-firmware
sudo cp zd1211_* /lib/firmware/zd1211

```[/INDENT]
[*]Unplug the F5D7050 device from the computer
[*]Make sure the driver is unloaded
[INDENT]```
sudo rmmod zd1211rw
```[/INDENT]
[*]Plug the usb device in again
[*]The driver should load using the new firmware and WPA will be supported. If for some reason the driver isn't loading either reboot, or run the following command:
[INDENT]```
sudo modprobe zd1211rw
```[/INDENT]
[/LIST]

---

