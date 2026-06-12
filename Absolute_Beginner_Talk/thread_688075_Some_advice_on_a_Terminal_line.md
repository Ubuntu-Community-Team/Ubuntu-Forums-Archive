---
title: "Some advice on a Terminal line"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-05
Hi there,

just seems (i hope) i need some help with some basic command line in Terminal.

I try to install an USB Adapter that will receive a Wireless N signal. I found a post that deals with it

[http://ubuntuforums.org/showthread.php?t=685793](http://ubuntuforums.org/showthread.php?t=685793)

It advices me to use ndiswrapper, which will use the windows xp driver to configure the device.

Here is the printout what i have done so far, the driver netmw245.inf is in my root directory call /andreas (that's me)

Here is some printout from the Terminal

andreas@andreas-laptop:~$ ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
andreas@andreas-laptop:~$ ndiswrapper -l
andreas@andreas-laptop:~$ ndiswrapper -i netmw245.inf
couldn't create /etc/ndiswrapper/netmw245: Permission denied at /usr/sbin/ndiswrapper line 194.
andreas@andreas-laptop:~$ sudo ndiswrapper -i netmw245.inf
installing netmw245 ...
couldn't find "MRVW245.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -
installation may be incomplete
andreas@andreas-laptop:~$ sudo ndiswrapper -i /andreas/netmw245.inf
driver netmw245 is already installed
andreas@andreas-laptop:~$ ndiswrapper -l
netmw245 : invalid driver!


So, i take it that the driver is in the wrong directory, please advice me what to do exactly....

Thanks
Andreas

---

### Post by spiderbatdad on 2008-02-05
i would recommend the graphical application ndisgtk in synaptic package manger

---

### Post by pebo on 2008-02-05
First you need to use sudo to install ndiswrapper. Second, you must be in the folder where the windows drivers are as ndiswrapper needs some of the additional files. (That's what the line "couldn't find "MRVW245.sys" in "."; make sure all driver files, including .inf, .sys (and any firmware files) are in "." -" is telling you. So to try again from the folder containing all the XP files first remove the incorrectly built driver:```
sudo ndiswrapper -r netmw245
sudo ndiswrapper -i netmw245.inf
sudo ndiswrapper -l *(output should give 'driver installed, hardware present')*
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```HTH

---

### Post by Djalmahal on 2008-02-05
So, if i try to install ndisgtk it ask me for the original ubuntu cd which i don't have, my internet is lousy, so if there is a way to just download it via the web that would be great, i looked around but couldn't find it.

I remove the driver, started ndiswrapper in the directory with the driver, it ndiswrapper finds the driver, but i still end up with the line

andreas@andreas-laptop:~$ sudo ndiswrapper -l
netmw245 : invalid driver!
andreas@andreas-laptop:~$ 


I downloaded the driver specifically for this hardware, so i don't really get what could be the problem, thanks for any advice

ANdreas

---

