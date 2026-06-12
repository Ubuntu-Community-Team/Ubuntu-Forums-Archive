---
title: "Bluetooth Connectivity"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-12-11
Guide Being Follow:
[http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux](http://arstechnica.com/journals/linux.ars/2007/12/10/using-a-bluetooth-phone-with-linux)
[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/bluetooth&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dp910%2Bbluetooth%2Bubuntu%2Bgnome%2Bobex%2Bvfs%26hl%3Den](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/bluetooth&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3Dp910%2Bbluetooth%2Bubuntu%2Bgnome%2Bobex%2Bvfs%26hl%3Den)

Cell Phone Brand:
Sony Ercisson P910i

OS:
Ubuntu 7.10

Bluetooth:
BlueSoliel USB Bluetooth Adapter

Problem:
When i search for device to pair with, my cellphone shows my dekstop system, but when i try to pair it, i see "Bonding in progress" for about 10 seconds and then "Bonding failed" resulting in no pairing. I have done all steps according to the guide. Even tried commenting out the passkey, but now use.
I even tried Blueman, yet no solution...
Any idea?


```

#
# HCI daemon configuration file.
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

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "Bluetooth Device id %d on %h";

	# Local device class
	class 0x000100;

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
}

```

---

### Post by shoaibi on 2007-12-16
I tried my Nokia 7600 and it can't even find if a bluetooth connection is available while my P910i can...

no help :(

---

### Post by philinux on 2007-12-16
My K810i can use my bluetooth adapter but I could only use it for transfering files. Decided to just use usb connection as it just mounts the phone card like a disk. and its much faster xfer rate.

---

