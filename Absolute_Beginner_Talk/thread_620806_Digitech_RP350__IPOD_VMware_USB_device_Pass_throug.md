---
title: "Digitech RP350 / IPOD VMware USB device Pass through??"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by MonibAhmed on 2007-11-23
My first post... I'm a noob to ubuntu... Been using it for about 1 month... I managed to install vmware-server and windows xp. I wanted to use cp for my windows only program. For example Digitech's X-edit program for my RP350, which is a guitar effects processor. I am unable to pass through my devices into vmware. I did a dmesg in terminal and here is what i got:

[ 2162.108000] usb 3-1: USB disconnect, address 2
[ 2169.152000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 2169.344000] usb 3-1: config 1 has an invalid interface number: 6 but max is 4
[ 2169.344000] usb 3-1: config 1 has an invalid interface number: 7 but max is 4
[ 2169.344000] usb 3-1: config 1 has no interface number 3
[ 2169.344000] usb 3-1: config 1 has no interface number 4
[ 2169.364000] usb 3-1: configuration #1 chosen from 1 choice
[ 2169.380000] 4:1:1: cannot get freq at ep 0x1
[ 2169.384000] 4:1:2: cannot get freq at ep 0x1
[ 2169.388000] 4:2:1: cannot get freq at ep 0x82
[ 2169.392000] 4:2:2: cannot get freq at ep 0x82

This is after I disconnect and reconnect my RP350. I tried getting vmware to recognize my IPod, but it won't recognize that either. I already tried the fix:

	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

Thanks for you help...

oh btw, I have a lenovo x61s, if that helps...

---

### Post by MonibAhmed on 2007-11-23
bump, anyone??? This forum is really busy...

---

