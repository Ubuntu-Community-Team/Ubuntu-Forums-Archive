---
title: "bluetoothing to computer from phone?"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-08-08
I can send stuff from my computer to my phone via bluetooth but I can't send stuff from my phone (when I tell my phone to find devices nothing comes up).

My hcid.conf file is:

#
# HCI daemon configuration file.
#
# $Id: hcid.conf,v 1.4 2004/04/29 20:14:21 holtmann Exp $
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
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	pin_helper /usr/bin/bluez-pin;
	#pin_helper /usr/bin/bluepin;

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
	class 0x100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	#
	#lm accept,master;
	#
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	#
	#lp hold,sniff;
	#
	lp rswitch,hold,sniff,park;

	# Authentication and Encryption
	#auth enable;
	#encrypt enable;
}


Thanks.

---

### Post by Lord Illidan on 2005-08-08
Try changing:

```
 
#lm accept,master;
#
lm accept;
[\CODE]

to

[CODE]lm accept,master;
``` only..

---

### Post by gammyhand on 2005-08-08
> **Lord Illidan]Try changing:

```
 
#lm accept,master said:**
> 

to

[CODE]lm accept,master;
``` only..
 Thanks...kind of there...I can now search for the device and find it, and pair with it in the bluetooth manager on my phone. But when I try to send the file (I have to go to the file and hit send via bluetooth) it says it can't find any bluetooth devices....any ideas?

---

### Post by gammyhand on 2005-08-08
[QUOTE=gammyhand]Thanks...kind of there...I can now search for the device and find it, and pair with it in the bluetooth manager on my phone. But when I try to send the file (I have to go to the file and hit send via bluetooth) it says it can't find any bluetooth devices....any ideas?[/QUOTE]
 bump because I am really needing to get some photos off my phone :o

---

### Post by gammyhand on 2005-08-09
[QUOTE=gammyhand]bump because I am really needing to get some photos off my phone :o[/QUOTE]
 anyone?

---

### Post by ltmon on 2005-08-09
I copied my hcid.conf directly from the documentation at [http://kde-bluetooth.sourceforge.net](http://kde-bluetooth.sourceforge.net) (they have a sample file).  There's only one kde specific bit in it (which is the pin helper) so the rest of it should be fine if you don't use kde.  Using this and a generic bluetooth usb dongle I had everything working perfectly with a SE k700i and a Nokia of some sort.

L.

---

### Post by SKLP on 2005-08-09
most bluetooth will AFAIK be fixed for breezy:

[https://wiki.ubuntu.com/BreezyGoals](https://wiki.ubuntu.com/BreezyGoals)

check "BluetoothSupport"

---

### Post by gammyhand on 2005-08-10
[QUOTE=SKLP]most bluetooth will AFAIK be fixed for breezy:

[https://wiki.ubuntu.com/BreezyGoals](https://wiki.ubuntu.com/BreezyGoals)

check "BluetoothSupport"[/QUOTE]
 I am very much looking forward to breezy!

---

