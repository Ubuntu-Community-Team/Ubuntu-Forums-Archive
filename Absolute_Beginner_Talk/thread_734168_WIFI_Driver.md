---
title: "WIFI Driver"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by trappleye on 2008-03-24
I just installed Ubuntu on my Desktop. Before I decided to install I was curious if the driver for my X-Micro WLAN 11b USB Adapter would be included. I booted first from the live CD (7.10, 32bit) and the USB adapter worked flawlessly. However, when I actually installed it the driver was not installed. I have searched everywhere for a driver, and I found this one [http://linux-lc100020.sourceforge.net/](http://linux-lc100020.sourceforge.net/), but when I tried to install it and run the make file it can't find the /etc/firmware directory that it needs to install in. I am curious if I can somehow get the driver off of the live cd? I don't have the ability to hook my computer directly to the router (Wired) Please help.

---

### Post by Sam Lars on 2008-03-24
When you install, can it see the card in the Network configuration?
I think you're looking for /lib/firmware

---

### Post by trappleye on 2008-03-24
Here is the make file. It looks like it is looking for the /etc/firmware directory. Should I change it to /lib/firmware?

#
#	Makefile for zd1201 firmware
#

FIRMWARE=zd1201.fw zd1201-ap.fw

INSTALL = cp -p -f

default: install

install:
	@echo -n "  INSTALL" ${FIRMWARE}
	@test -d /etc/firmware \
	 && $(INSTALL) ${FIRMWARE} /etc/firmware \
	 && echo " =>" /etc/firmware/ \
	 || test -d /usr/lib/hotplug/firmware \
	 && $(INSTALL) ${FIRMWARE} /usr/lib/hotplug/firmware \
	 && echo " =>" /usr/lib/hotplug/firmware/ \
	 || ( echo && echo "Failed:  No firmware directory found" && false )

---

