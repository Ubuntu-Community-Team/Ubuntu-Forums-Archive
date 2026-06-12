---
title: "Windows install with USB DVD drive"
date: 2012-06-11
forum: Any Other OS
---

### Post by blairm on 2012-06-11
Hi,

Trying to install Windows 7 on one of my computers which is currently running Ubuntu (want to use this one for gaming).
I'm using a USB DVD drive for the install but it's not working.
I've changed the boot order in the bios to make usb dvd first boot, and when that didn't work tried dvd as first boot - still no luck.
Is there something obvious I'm doing wrong/forgetting to do? 

Blair

---

### Post by evilsoup on 2012-06-11
Well my laptop actually ignores the boot order set up in the BIOS; when I want to boot from a memory stick or something, I have to press ESC during startup.

Could be something like that?

---

### Post by blairm on 2012-06-11
Just tried booting a Slackware disc too, no joy. It's like the system doesn't see the drive.
The light on the drive goes on for a second when I put the disc in then it goes off and nothing hapens - could that mean the drive is faulty? Just bought it a couple of hours ago.

---

### Post by C.S.Cameron on 2012-06-11
If all else fails, try a boot manager like plop.

---

### Post by uRock on 2012-06-11
Moved to *Other OS/Distro Talk*.

---

### Post by oklokl on 2012-06-11
I'm using is a way ..

## remove mbr..
## fomat usb..
sudo apt-get install gparted

gparted -> new mbr and.. ntfs-3g format..


Try installing usb as below.

[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)
For details, please see here

 [https://launchpad.net/~colingille/+archive/freshlight]("https://launchpad.net/%7Ecolingille/+archive/freshlight")



```
sudo add-apt-repository ppa:colingille/freshlight 

sudo apt-get update 
sudo apt-get install winusb
```
Since WinUSB also works from the command line, you can create a  Windows 7 or Windows Vista USB installer by following the command line  format given below:
 ```
sudo winusb --format <iso path> <device> 
```Once the USB is formatted using the above method, install a Windows partition and edit the Master Boot Record:
 ```
sudo winusb --install <iso path> <partition>
```

---

