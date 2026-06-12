---
title: "hlep with buetooth keyboard"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-09-08
im having touble getting my bluetooth keyboard to work. I can do this:

$ hcitool scan
Scanning ...
        00:16:38:EC:27:0D       Think Outside Keyboard

but I cant connect:
$ hidd --connect 00:16:38:EC:27:0D
HID create error 13 (Permission denied)


here is /etc/bluetooth/hcid.conf

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
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# PIN helper
	# pin_helper /usr/bin/pinwrapper;
	#pin_helper /usr/local/sbin/mypin

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
 device 00:16:38:EC:27:0D {
     name "Think Outside Keyboard";
     auth disable;
     encrypt disable;
 }



here is my /etc/default/bluez-utils

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
#HIDD_OPTIONS="--server --search"
HIDD_OPTIONS="--connect 00:16:38:EC:27:0D --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i 00:16:38:EC:27:0D --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

############ COMPATIBILITY WITH OLD BLUEZ-PAN
# Compatibility: if old PAN config exists, use it
# rather than this file.
if test -f /etc/default/bluez-pan; then
    . /etc/default/bluez-pan
    return
fi
############

############ DUND
#
# Run dund -- this allows ppp logins. 1 for enabled, 0 for disabled.
DUND_ENABLED=0

# Arguments to dund: defaults to acting as a server
DUND_OPTIONS="--listen --persist"

# Run dund --help to see the full array of options.
# Here are some examples:
#
 


any help would be great thanks!

---

### Post by jinxjinx on 2006-09-14
ok i fixed the problem. now my thinkoutside bluetooth keybaord works perfectly wiht linux!

i changed this line from 
device 00:16:38:EC:27:0D {
name "Think Outside Keyboard";
auth disable;
encrypt disable;
}

to 
device 00:16:38:EC:27:0D {
name "Think Outside Keyboard";
}

---

