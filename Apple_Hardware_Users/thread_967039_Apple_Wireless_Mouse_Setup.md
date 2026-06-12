---
title: "Apple Wireless Mouse Setup"
date: 2008-11-01
forum: Apple Hardware Users
---

### Post by Acoshi on 2008-11-01
I recently upgrade from Hardy Heron to Intrepid Ibex and was having issues connecting my apple bluetooth keyboard and mouse.

After doing extensive research on the issue I was able to solve the problem of pairing my keyboard so that every time the computer restarts its is immediately noticed by my MacBook.

But for some reason I am still having trouble pairing my apple mouse after restart. The system doesn't even recognize it.

I made sure that the batteries were new and I also reset it a number of times with the same result.

This is how my hcid.conf file looks:

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
	passkey "0000";
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
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
device 00:1F:5B:AC:77:1E {
name "Mighty Mouse"
auth enable;
encrypt enable;
}
device 00:1E:52:FB:B0:5E {
name “Apple Wireless Keyboard”;
auth enable;
encrypt enable;
}

Hopefully this helps

Thanks in advance

---

### Post by Acoshi on 2008-11-01
bump

---

### Post by cyberdork33 on 2008-11-01
does the bluetooth applet not work to connect your mouse?

Helpful info on the keyboard though...

---

### Post by Acoshi on 2008-11-01
Should I give more info of the situation?

---

### Post by cyberdork33 on 2008-11-01
> **Acoshi said:**
> Should I give more info of the situation?
maybe on the keyboard setup...

Have you tried the Bluetooth Applet near the clock to setup your Mouse? Most people have reported that working.

---

### Post by mjrempes1 on 2008-11-02
Hi I've got a very similar issue.

I had mamanged to install the wireless aluminium keyboard and mighty mouse with bluetooth on ubuntu 7.1

However two main issues. First of all I could not click the mouse. Secondly neither device would connect after I restarted the computer.

Since then I've reinstallaed, made sure everything is update, and am hoping someone can help me figure out how to well primarily in this cae get my mouse to connect and work properly and stay that way when i restart my computer.

If someone on here is able to help me get the keyboard working, that would be great as well.

---

### Post by Acoshi on 2008-11-02
The bluetooth applet doesn't work with my mouse. For some reason it doesn't even noticed my mouse.

I made sure that the MAC address on my mouse was correct as well.

Here is the bluetooth file:

# Defaults for bluez

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
BLUETOOTH_ENABLED=1

# This setting will switch HID devices (e.g mouse/keyboad) to HCI mode, that is
# you will have bluetooth functionality from your dongle instead of only HID.
# Note that not every bluetooth dongle is capable of switching back to HID
# mode, see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=355497)
HID2HCI_ENABLED=0
HID2HCI_UNDO=0
HIDD_OPTIONS="--connect 00:1F:5B:AC:77:IE"
HIDD_OPTIONS="--connect 00:1E:52:FB:B0:5E --server"
DUND_ENABLED=1
DUND_OPTIONS="--listen --persist --msdun call treo"
HIDD_ENABLED=1

The mac address ending in IE is for my mouse.

I double checked the settings with my keyboard and everything is exactly matching. Right now I am running out of different things to try.

Hopefully this helps

---

### Post by Acoshi on 2008-11-03
bump

---

### Post by cyberdork33 on 2008-11-03
This might be helpful. 
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

note that the hidd binary is now in the bluez-compat package so you will have to install that to use hidd.

---

### Post by Acoshi on 2008-11-06
I have installed Bluez but no luck the keyboard can pair with the computer but the mighty mouse still can't. BlueProximity can't even locate it.

---

### Post by Acoshi on 2008-11-06
I tried using hidd --connect command and ran into this error:
Can't create hidd control channel connection refused.

Does anyone know what this could mean and how to fix it?

---

### Post by hyperboloid on 2008-11-06
There is a known bug in Bluetooth on the new Intrepid release, see [http://ubuntuforums.org/showthread.php?t=966436]("http://ubuntuforums.org/showthread.php?t=966436").

Have you tried the workaround suggested there? That worked for me. 

Specifically, I was able to initially pair the Mighty Mouse after doing an "hciconfig hci0 reset" but lost the mouse after every reboot. I was able to re-pair the mouse only after going into Bluetooth Preferences (right-click on BT icon, or use System -> Preferences -> Bluetooth), deleting the mouse, and then going through the whole setup process anew. 

The suggested workaround was to click on "Hidden" and then select "Always Visible" in Bluetooth Preferences, instead of deleting the mouse. After doing that, my Mighty Mouse now survives reboots! I have no idea why this helps.

I'm using a fresh install of the 8.10 release, and I have not modified any of the Bluetooth config files, nor have I installed other BT packages.

---

