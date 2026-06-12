---
title: "Problems to connect a bluetooth Apple keybord on MacbookPro"
date: 2007-09-19
forum: Apple Intel Users
---

### Post by BobOnMac on 2007-09-19
Hi everybody,
I installed Kubuntu Feisty 7.04 on a MacBookPro a few months ago and almost everything works fine. However I have a problem to connect a bluetooth Apple keyboard on MacbookPro.
I went around a number of posts in forums and learnt much on how to configure it 
As an example, my bluetooth Apple mouse works fine but my keyboard refuses to connect though perfectly detected.

[I]kuszel@castafiore:~$ hcitool scan
Scanning ...
        00:14:51:C0:6A:90       Souris de kuszel
        00:0A:95:45:D7:7B       Apple Wireless Keyboard
kuszel@castafiore:~$[/I]

An attempt to connect the keyboard yields this :

[I]kuszel@castafiore:~$ sudo hidd --search
Searching ...
        Connecting to device 00:0A:95:45:D7:7B[/I]
(ihere I insert a 4 digit PIN number + CR with the Apple keyboard itself and after 30 s approx., I get )
[I]
Can't get device information: Function not implemented
kuszel@castafiore:~$  [/I]                          

Could someone please help me ? Did I forget to load a package or is the Apple keyboard really something special ?

Thanks

---

### Post by cyberdork33 on 2007-09-19
Here is the information I used to do it before. I hope it is helpful:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by BobOnMac on 2007-09-19
I already read this information sheet, and precisely used it before joining the forum. Unfortunately, the problem seems to originate from some other reason.
Because my keyboard is detected but cannot connect.

Thank you for your help anyway

---

### Post by cyberdork33 on 2007-09-19
> **BobOnMac said:**
> I already read this information sheet, and precisely used it before joining the forum. Unfortunately, the problem seems to originate from some other reason.
Because my keyboard is detected but cannot connect.

Thank you for your help anyway
I haven't tried this in a long time, but I will make an attempt later today. I am on gutsy though...

---

### Post by BobOnMac on 2007-09-19
Thanks

---

### Post by cyberdork33 on 2007-09-20
> **BobOnMac said:**
> ThanksWell that didn't help. I only ran the '*sudo hidd --search*' command and it found and connected my keyboard without hesitation. I did come across this thread though which seems more applicable than the wiki page.
[http://ubuntuforums.org/showthread.php?t=224673](http://ubuntuforums.org/showthread.php?t=224673)

---

### Post by BobOnMac on 2007-09-20
Well I also knew this thread, and it does not hael. Perhaps have incorrect config files. Here are my
* /etc/default/bluetooth*

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=0
# HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="--connect 00:14:51:C0:6A:90 --connect 00:0A:95:45:D7:7B --server"
#
# remove '--master' if you're having trouble working with Ericsson
# T630 phones with hidd operational at the same time.

and * /etc/bluetooth/hcid.conf*


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
	#security user;
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "0000";
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
	discovto 0;

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
	#encrypt	enable;
}

device 00:14:51:C0:6A:90 {
	name "Souris de kuszel";
}

device 00:0A:95:45:D7:7B {
	name "Apple Wireless Keyboard";
	auth enable;
	encrypt enable;
}


Perhaps it may help
Thanks

---

### Post by ivelasco on 2007-09-20
I believe that in the /etc/default/bluetooth you must change from HIDD_ENABLED=0 to HIDD_ENABLED=1 and define the devices in this file,not in hcid.conf.This is at least how I do it and the Three Bluetooth devices that ever connect worked.For apple devices you must define(I ve seen that you are done)the 

auth enable;
encrypt enable;

paramams at hcid.conf

For me two packets have been very usefull:

bluetooth
bluez-gnome(this is the applet that ask to you for the pin)

good luck!

---

### Post by cyberdork33 on 2007-09-20
> **ivelasco said:**
> I believe that in the /etc/default/bluetooth you must change from HIDD_ENABLED=0 to HIDD_ENABLED=1 and define the devices in this file,not in hcid.conf.I thought that was the case also, but the thread that I last linked to says the opposite. Either way, it worked for me the way the thread set it up, as well as without making any changes at all, but I am never getting prompts for a PIN. Do you know how I could have disabled that? Maybe I should find out how to completely reset my keyboard.
The bluez-gnome package helps considerably

---

### Post by sunbird on 2008-03-29
Hi...

Still working on resolving a handful of issues on my new install. Bluetooth isn't working at all for me. I get this output after a fresh boot:

```

~$ hcitool scan
Device is not available: No such device

```

Here's my /etc/default/bluetooth:

```

# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
HIDD_ENABLED=1
HIDD_OPTIONS="--master --server"
# to make hidd always use a particular interface, use something
# like this, substituting the bdaddr of the interface:
# HIDD_OPTIONS="-i AA:BB:CC:DD:EE:FF --server"
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
# Connect to any nearby host offering access
# DUND_OPTIONS="--search"
#
# Connect to host 00:11:22:33:44:55
# DUND_OPTIONS="--connect 00:11:22:33:44:55"
#
# Listen on channel 3
# DUND_OPTIONS="--listen --channel 3"

# Special consideration is needed for certain devices. Microsoft
# users see the --msdun option.  Ericsson P800 users will need to
# listen on channel 3 and also run 'sdptool add --channel=3 SP'

############ PAND
#
# Run pand -- ethernet: creates new network interfaces bnep<N>
# that can be configured in /etc/network/interfaces
# set to 1 for enabled, 0 for disabled
PAND_ENABLED=0

# Arguments to pand
# Read the PAN howto for ways to set this up
# http://bluez.sourceforge.net/contrib/HOWTO-PAN
PAND_OPTIONS=""

# example pand lines
#
# Act as the controller of an ad-hoc network
# PAND_OPTIONS="--listen --role GN"
#
# Act as a network access point: routes to other networks
# PAND_OPTIONS="--listen --role NAP"
#
# Act as a client of an ad-hoc controller with number 00:11:22:33:44:55
# PAND_OPTIONS="--role PANU --connect 00:11:22:33:44:55"
#
# Connect to any nearby network controller (access point or ad-hoc)
# PAND_OPTIONS="--role PANU --search"

############ SDPTOOL
# this variable controls the options passed to sdptool on boot, useful if you
# need to setup sdpd on boot.
# options are ;-separated, i.e. for every ; an sdptool instance will be
# launched
#
# examples:
# SDPTOOL_OPTIONS="add --channel=3 SP" # ericsson P800 serial profile
# SDPTOOL_OPTIONS="add --channel=8 OPUSH ; add --channel=9 FTRN" # motorola
#                                             # object push and file transfer
SDPTOOL_OPTIONS=""

```

And here is /etc/bluetooth/

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
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "0000"
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm master;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

device ____ {

name "apple bluetooth keyboard";

auth enable;

encrypt enable;

}

device ____ {

name "Walrus";

auth enable;

}

device ____ {

name "Bluetooth Travel Mouse";

}

```

My noob analysis is that it doesn't see my bluetooth card at all. Any ideas how to fix it?

**EDIT:**
I tried running apt-get remove --purge bluetooth bluez-gnome and then reinstalled, changed HIDD_ENABLE=1 and then I get this curious message:

```

~$ sudo /etc/init.d/bluetooth stop
 * Stopping Bluetooth services                              [ OK ] 
~$ sudo /etc/init.d/bluetooth start
 * Starting Bluetooth services
     Can't listen on HID control channel: Address already in use

```

Any ideas? Really missing my keyboard/mouse.

---

### Post by sunbird on 2008-04-01
**Bump**

Any help? This issue is driving me crazy. I've scoured the forums and feel like I've tried everything. I know this *can* work and I'm probably missing something really obvious.

---

### Post by cyberdork33 on 2008-04-01
I would just wait. The bluetooth stack is completely changed in Hardy so anything determined now will be invalid in a couple of weeks.

---

### Post by george.talusan on 2008-04-02
If the keyboard is detected but doesn't work then the pairing process failed.

Press the side button on wireless keyboard to reinitiate the pairing process.  When the light stops blinking, type in your password, and hit enter.

If it doesn't work then try a few times.

---

### Post by sunbird on 2008-04-03
> **george.talusan said:**
> If the keyboard is detected but doesn't work then the pairing process failed.

Press the side button on wireless keyboard to reinitiate the pairing process.  When the light stops blinking, type in your password, and hit enter.

If it doesn't work then try a few times.

No, the problem for me is more fundamental:

```

$ hcitool scan
Device is not available: No such device

```

---

### Post by cyberdork33 on 2008-04-03
> **sunbird said:**
> No, the problem for me is more fundamental:

```

$ hcitool scan
Device is not available: No such device

```
I think it is not detecting your bluetooth card in the Mac for some reason. can you make sure that blueotooth is running:

```
sudo /etc/init.d/bluetoooth start
```

---

### Post by sunbird on 2008-04-03
I agree. That's definitely the problem. I just don't understand why it's happening because I had the bluetooth working on this machine, under Ubuntu 7.10x64, when I installed from the Live CD. It's only after I did a reinstall from the Alternate CD that it didn't work.

```

:~$ sudo /etc/init.d/bluetooth start
 * Starting Bluetooth services                                                           [ OK ] 
~$ hcitool scan
Device is not available: No such device

```

Does the bluetooth adapter normally show up when running lspci -vv | grep blue or lsusb -vv | grep blue? Because both of those commands yield no results for me.

I should add that bluetooth works just fine in OS X, so it's not a problem with the adapter.

---

### Post by cyberdork33 on 2008-04-03
it should be in lsusb.

---

### Post by sunbird on 2008-04-03
Figured it out. 

I found the device when I ran lsusb -v | grep **-i** blue (duh! ignore case).

Bluetooth modules were running:

```

$ lsmod | grep blue
bluetooth              63876  5 hidp,rfcomm,l2cap

```

**But, hci_usb was _NOT_ running.**

```

sudo modprobe hci_usb
$ lsmod | grep blue 
bluetooth              63876  8 hci_usb,hidp,rfcomm,l2cap

```

Will add that to /etc/rc.local. Phew.

---

### Post by cyberdork33 on 2008-04-03
> **sunbird said:**
> **But, hci_usb was _NOT_ running.**

```

sudo modprobe hci_usb
$ lsmod | grep blue 
bluetooth              63876  8 hci_usb,hidp,rfcomm,l2cap

```Will add that to /etc/rc.local. Phew.

That sounds like that's it.

I think you can just add hci_usb to /etc/modules

---

### Post by russo.mic on 2008-04-20
Well,  I'm in the same boat.  Macbook Pro C2D, (pre santa rosa), and I can see the mouse, with hcitool scan, but no matter what I do I can't get it to pair.  The computer even behaves as if it pairs, but to no avail!  Tried manually editing the config files, tried just using the GUI tools, and  nothing works.  Maybe waiting is the best thing, but I hate giving up!  Anyone else have any ideas?  

Russo

---

