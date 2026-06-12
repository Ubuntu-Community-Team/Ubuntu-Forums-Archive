---
title: "Bluetooth"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-02-10
Does anyone know how I can get Bluetooth working on my laptop please?

---

### Post by Brunellus on 2006-02-10
you will need to install the gnome bluetooth tools and the necessary libraries. 

sudo apt-get install gnome-bluetooth

should get you going.  Alternatively, select gnome-bluetooth in Synaptic.

---

### Post by Pragmatist on 2006-02-10
Check in synaptic to see if the gnome-bluetooth package is installed.  If it isn't, install it and see if it helps.  KDE has its own tools for bluetooth and you'll see its package in synaptic too.

If  that doesn't work, try ```
man -k bluetooth
```  and ```
man hcitool
```  Also, try ```
locate bluetooth
```  if you already did ```
updatedb
``` as root, you should get alot of stuff when you try "locate bluetooth".  If I were you, I would google at [www.google.com/linux](www.google.com/linux) and type in my bluetooth specs to see what the name of the driver is.  The do ```
lsmod
``` to see if it is at least loading.  If it isn't loaded, but is on your system (at something like /lib/modules/2.6.12-8-386/kernel/drivers/bluetooth ) then do ```
insmod <name of your driver>
```  If all of that works, then it is just a matter of making sure the module loads every time you reboot.

---

### Post by Dr Von Bon Bon on 2006-02-11
Hi,

Thanks, I found this webpage about my laptop with bluetooth:

[http://www.cavecanen.org/linux/x300/#bluetooth](http://www.cavecanen.org/linux/x300/#bluetooth)

but I dont' understand what I have to actually do.

Could someone please tell me what to do please?

---

### Post by Garyu on 2006-02-11
[http://www.ubuntuforums.org/showthread.php?t=75978&highlight=gnome+bluetooth](http://www.ubuntuforums.org/showthread.php?t=75978&highlight=gnome+bluetooth)

Check this thread out. KDE bluetooth deamon (kbluetoothd) seems to be more developed than gnome-bluetooth according to this guy. And it worked fine for me, up until the PIN number. Maybe it will be easier for you to get it to work if you have different hardware than I do.

---

### Post by Dr Von Bon Bon on 2006-02-11
The same thing happens to me.

It works fine up until the PIN number at which it says the connection failed.

Does anyone know how I can get this to work please?

---

### Post by Pragmatist on 2006-02-11
Send us the output of this file: ***/etc/bluetooth/hcid.conf***

---

### Post by Dr Von Bon Bon on 2006-02-11
here we go:


```
#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.7 2004/12/13 14:16:03 holtmann Exp $
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bluez-pin;

	# D-Bus PIN helper
	#dbus_pin_helper;
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption (Security Mode 3)
	#auth enable;
	#encrypt enable;
}

```

I hope that helps

---

### Post by Pragmatist on 2006-02-11
If it were me, and I haven't done this specific thing before, I would try disabling certain features to see if I can get the bluetooth device to work in the simplest situation possible.  Then, I'd at least know that the driver was available and the device works.  After that, you could figure out about the PIN thing.

So, I would try setting Security to none:
        #  Security Manager mode
        #   none - Security manager disabled
        #   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security none;

If you can't afford to try that because what your doing needs to be highly secure at all times, then see if you can set it to: auto  Check out /etc/bluetooth/pin  to see your local pin.

Again, this is just for testing purposes.  I would see what others have to say, but I would also play with the config files and read the man pages I referred you to.

---

### Post by Dr Von Bon Bon on 2006-02-12
Thanks, I'll try doing that.

I've had another problem that is when I start the bluetooth up it now says thatit "Failed To Connect To The SDP Server".

Any help pleasE?

---

