---
title: "USB dialup modem problem"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by cklinux on 2007-07-15
Hello I read dialup howto run scanmodem downloaded sl drivers run gnome-ppp but nothing helped.
My problem is as following : I want to use a USB dial up modem to send faxes
the modem is recognised by ubunty device manager as Soft56k
/sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0
/org/freedesktop/Hal/devices/usb_device_483_7554_noserial
/dev/bus/usb/003/002 usbraw device
usb vendor SGS Thomson Microelectronics
gnome-ppp or mvdial don't detect it.
also efax-gtk or gfax don't work can't find the modem in dev/modem nor if I put one of the above
addresses.
I tried mounting the device but I get the error not a block device (which I guess means that it is not a hdd)
am at a loss!
I just need to use it occasionaly for sending faxes. How can I map the usb to a virtual device or to a  serial port so that it can be used with efax??
Thanks everybody

---

### Post by oilchangeguy on 2007-07-15
your best bet, is probably going to be using a serial port external modem. i'd suggest ebay as a source for one.

---

### Post by oilchangeguy on 2007-07-15
i just did a quick ebay search. and this seems to be the only one listed.
[http://cgi.ebay.com/External-Serial-Port-DIAMOND-SUPRA-EXPRESS-56K-Modem_W0QQitemZ270141894609QQihZ017QQcategoryZ14920QQrdZ1QQssPageNameZWD1VQQcmdZViewItem](http://cgi.ebay.com/External-Serial-Port-DIAMOND-SUPRA-EXPRESS-56K-Modem_W0QQitemZ270141894609QQihZ017QQcategoryZ14920QQrdZ1QQssPageNameZWD1VQQcmdZViewItem)

---

### Post by cklinux on 2007-07-15
thanx but first I would rather not shell out money for this and secondly I have successfully used the modem in the past in Ubuntu, just don't remember if I had fidled with settings or not then !

---

### Post by bme on 2007-07-15
try wvdial config and see if your usb modem is detected....since you have used it previously on ubuntu then no reason why you can't use it on a newer ubuntu version...

---

### Post by cklinux on 2007-07-15
chris@chris-desktop:~$ wvdial config
--> WvDial: Internet dialer version 1.56
--> Warning: section [Dialer config] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
chris@chris-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
chris@chris-desktop:~$ 
it has worked again in the SAME Ubuntu version in a previous instalation of 6.10 now I don't know
why it does not work. I guess I have to map somehow usb to dev/modem or to serial but I don't know how as I said in first post.

---

### Post by Bartender on 2007-07-15
I don't think that's the right wvdial commands.
Try the ones I listed in post #3
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

Also do the first part, the part about creating the /etc/resolv.conf file.

---

