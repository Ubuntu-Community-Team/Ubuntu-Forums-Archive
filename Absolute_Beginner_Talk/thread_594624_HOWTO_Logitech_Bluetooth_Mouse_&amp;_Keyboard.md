---
title: "HOWTO: Logitech Bluetooth Mouse &amp; Keyboard"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by bubbalouie on 2007-10-28
This is an edited version of the following HOWTO [link]("http://ubuntuforums.org/showthread.php?p=2017615"), full credit goes to the original author, I have only updated a few file names and made some other minor alterations. Please note I can not guarantee this will work for your system, you should always backup any files before changing them.

I have a bluetooth Logitech DiNovo keyboard and MX1000 mouse, as well as a bluetooth travel mouse and I use Kubuntu 7.10 with a VAIO laptop. This tutorial should help you getting your keyboard and mouse up and running (and automatically reconnecting after you reboot).

This tutorial is an adapted version of this forum thread by boneill.

[SIZE="6"]Getting Started[/SIZE]

We need the MAC address (e.g. 00:00:00:00:00) of the mouse and keyboard. I shall use KEYBOARD_ADDR and MOUSE_ADDR where you should find the addresses for the keyboard and mouse respectively. Press the button on the mouse that makes it visible to be found by the computer. Do the same for the keyboard. Now open a terminal window and run the following command:

```
 user@computer:~$ hcitool scan
 Scanning ...
         KEYBOARD_ADDR1       Logitech diNovo Keyboard
         KEYBOARD_ADDR2       Logitech Mediapad
         MOUSE_ADDR1          Logitech MX1000 mouse
         MOUSE_ADDR2          Bluetooth Travel Mouse
 user@computer:~$
```

[SIZE="6"]Adding the Keyboard and Mouse[/SIZE]

Now we need to add the keyboard and mouse to the bluetooth configuration files. Run the following command to pop up kate:

```
 user@computer:~$ sudo kate /etc/bluetooth/hcid.conf
```

You may be asked for your password, this is because we used sudo.

At the end of the file, add the following (replacing the device addresses you discovered in the previous step):

```
device KEYBOARD_ADDR1 {
	name "Logitech diNovo Keyboard";
	auth enable;
	encrypt enable;
}
 
device KEYBOARD_ADDR2 {
	name "Logitech Mediapad";
	auth enable;
	encrypt enable;
}

device MOUSE_ADDR1 {
	name "Logitech MX1000 mouse"
}

device MOUSE_ADDR2 {
	name "Bluetooth travel mouse"
}
```

Now you need to restart the bluetooth subsystem so that it refreshes it's configuration file.

```
 user@computer:~$ sudo /etc/init.d/bluetooth restart
  * Restarting Bluetooth services... [ ok ]
```

[SIZE="6"]Pairing the Devices[/SIZE]

You now need to pair the devices with the computer. Do not press any buttons on the keyboard as we'll need to use it to enter a passcode so we can pair. Run the following command:

```
 user@computer:~$ sudo hidd --search
 Searching ...
         Connecting to device MOUSE_ADDR1
         Connecting to device MOUSE_ADDR2
         Connecting to device KEYBOARD_ADDR1
         Connecting to device KEYBOARD_ADDR2
 user@computer:~$
```

They could pair with the computer in any order, you will need to remember which one is the keyboard. As soon as Connecting to device KEYBOARD_ADDR appears you must enter a PIN code into the keyboard. It must consist of numbers not using the numpad, I can't remember how many you can use, but somewhere between 4 and 8 should be fine. Type this number in to the keyboard and press Return. I did not need to perform this step, however some devices may require it.

A window should pop up on your computer asking you for the number you just entered on the keyboard. Again I did not need to perform this step, however some devices may require it.

[SIZE="6"]Connecting at Boot[/SIZE]

In order to get your mouse and keyboard to connect at boot time do the following:

```
 user@computer:~$ sudo kate /etc/default/bluetooth
```

Find the line with the following:

```
 HIDD_ENABLED=0
```
 
Change it to:

Code:

```
 HIDD_ENABLED=1
```

Now reboot and hopefully they'll automatically connect (give them a few seconds to connect after you move the mouse/press a key).

Sometmies a device may not connect due to new batteries or some other malfunction, the following command should force a reconnect:

```
user@computer~:$ sudo hidd --search
```

[SIZE="6"]Enabling Extra Mouse Buttons[/SIZE]

Finally, in order to enable the back and forwards buttons on my MX1000 mouse I altered my xorg.conf file as follows:

```
user@computer~: sudo kate/etc/X11/xorg.conf
```

Find the section that for the 'Configured Mouse' and replace it with the following:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
EndSection
```

Now save the file and close kate. Your extra buttons should now work when you restart X (ctrl+alt+backspace). You will find a tool in the KDE menu system group group called kbluetooth, this will provide a facility for connecting to devices such as phones for sending files.

[SIZE="6"]Reference Files[/SIZE]

For reference (with some address changes etc) here is what my */etc/bluetooth/hcid.conf* looks like:

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


device 00:07:61:33:EE:EE {
	name "Logitech diNovo Keyboard";
	auth enable;
	encrypt enable;
}

device 00:07:61:33:EE:EE {
	name "Logitech Mediapad";
	auth enable;
	encrypt enable;
}

device 00:07:61:33:EE:EE {
	name "Logitech MX1000 mouse"
}

device 00:07:61:3f:EE:EE {
	name "Bluetooth travel mouse"
}

```

And my */etc/default/bluetooth* file:

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

Finally */etc/X11/xorg.conf* file:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons" "7"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig" "on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G72M [GeForce Go 7400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [GeForce Go 7400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by Delvien on 2007-10-28
Nice post, I'll test it out on my Mx5000 mouse. (forward button not working presently ) everything else tho...

---

### Post by i,bigfoot on 2007-11-03
Hi there..

thanks for the post on howto setup logitech bluetooth stuff! 

I ran into some problems following this guide, well a single problem, so i thought i would share experience.  (Ubuntu 7.10 - Intel E6600 - Asus P5W DH - Logitech DiNovo keyboard, mouse, mediapad)

the hcitool scan command wouldn't find any devices, hence i had no MAC address to enter into the config file.  

My workaround is simple.  When I get to the login screen on startup I remove and plug back in the USB bluetooth dongle.  Not sure exactly what this does, but after a couple of seconds my devices are recognised.  

If I do a CTRL-ALT-BACKSPACE i do not need to do this, keyboard mouse and media pad are recognised immediately. 

cheers,
Troy

---

### Post by Leonivek on 2007-11-22
I have the same problem... the hcitool scan command does not give me any results... just tells me "Device is not available: No such device".  I cannot figure out what my MAC addresses are for my MX5000 keyboard and mouse.  They work after I unplug my Bluetooth adapter and re-plug it, but I don't want to have to do this every time I reboot.  Obviously, CTRL-ALT-BACKSPACE doesn't work cause the keyboard doesn't work!

Also, hidd --search doesn't give me anything.

Does anyone know if there's another way to get the MAC addresses of my devices so I can configure my files?

Thanks!

[EDIT]  Never mind... I got my addresses from within Windows.

---

### Post by bubbalouie on 2007-11-26
It should be written on the underside of each device, also, I have a suspicion that USB dongles only work when plugged in after boot up.

---

### Post by brutusbucki2 on 2008-01-08
Where exactly do I find the mac address for my MX1000

---

### Post by lithorus on 2008-01-09
Thanks for the guide, works pefrectly with the logitech mediaboard pro (for the PS3) aswell.
On my desktop using Hardy. Will test later today with my VAIO laptop.

---

### Post by johnnypy on 2008-01-10
Could you give me details of what you did exactly to make this work? I am using Gutsy Gibbon, on a PS3 with a logitech mediaboard pro, and have followed all the posts, but cannot get the connection to stick on reboot. I keep getting an obex error message when I check the connection with the bluetooth prefernce settings. Hoping you can help - I am new to PS3, linux and ubuntu.

---

### Post by TheJacksonians on 2008-01-11
First, thanks for the instructions. I have a MX1000 mouse and MX5000 keyboard. The mouse connects fine at reboot, however, the keyboard does not. I am also not asked for any sort of passcode.

I'm running newly installed 7.10.

Is there something I'm missing? Thanks for your help!

---

### Post by bubbalouie on 2008-01-14
> **brutusbucki2 said:**
> Where exactly do I find the mac address for my MX1000
Look under the mouse, you will find a label, the mac address is labeled BTA, hope this helps.

---

### Post by bubbalouie on 2008-01-14
> **lithorus said:**
> Thanks for the guide, works pefrectly with the logitech mediaboard pro (for the PS3) aswell.
On my desktop using Hardy. Will test later today with my VAIO laptop.
Glad to help :)

---

### Post by bubbalouie on 2008-01-14
> **TheJacksonians said:**
> First, thanks for the instructions. I have a MX1000 mouse and MX5000 keyboard. The mouse connects fine at reboot, however, the keyboard does not. I am also not asked for any sort of passcode.

I'm running newly installed 7.10.

Is there something I'm missing? Thanks for your help!
Sorry, nothing immediately springs to mind, starngely on my GF's computer a hard reboot is needed for things to work. If you are okay with sharing the relevant files up here:

/etc/bluetooth/hcid.conf
/etc/default/bluetooth

I might be able to help, if I can't maybe someone else will, I was never asked for a pass key on the keyboard either, however my system is configured to use a default value, though I did intially think it was odd never being asked to enter the key via the keyboard.

---

### Post by mesilliac on 2008-01-14
Nice guide :). Just a quick question. Do you have the horizontal scroll via touchpad working on your DiNovo keyboard?

I just plugged mine in and almost everything worked, but it might be worth going to more effort to set it up if I could get 4-way scrolling to work.

---

### Post by bubbalouie on 2008-01-15
> **mesilliac said:**
> Nice guide :). Just a quick question. Do you have the horizontal scroll via touchpad working on your DiNovo keyboard?

I just plugged mine in and almost everything worked, but it might be worth going to more effort to set it up if I could get 4-way scrolling to work.
No touch pad for me sorry, I have the older version, however, from memory the xorg.conf file contains various lines to do with horizontal scrolling, an older version of the file had a *option HorizontalDelta "0"*, when the zero was changed to a one the horizontal scrolling worked on my synaptics touch pad when X was restarted and the setting would stick.

Perhaps if you find a similar line and edit it you may have some luck, though I am unsure of what device description the Edge would fit. if you're lucky synaptics will do.

My xorg has the following:

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
    Option         "MaxTapTime" "0"
EndSection

I have only disabled tapping as horizontal scrolling bugged me and the format has changed a little, but perhaps a * Option         "HorizEdgeScroll" "1"* will sort things out, though I can't say for sure.

Good luck

---

### Post by alamarco on 2008-01-17
Thanks for the guide. Is there any other way to determine the MAC address of the devices?

Under my mouse and keyboard there are black marks for what I assume is the seriel #'s. My keyboard and mouse are refurbished. These black markings cover part of the BTA section so I'm unable to determine the MAC address in this manner.

edit: Just to let you know, I ended up getting it working with hcitool. I thought I just had to press the Connect button, but instead I had to hold it down for it to be recognized during the searching process.

edit2: Woke up this morning and the devices are no longer connected. When I do a reconnect with 'sudo hidd --search' it doesn't find the devices. Is there anyway to make the connection stay? Both my keyboard and mouse are no longer connected.

---

### Post by Philio on 2008-01-24
Hi, wondering if anyone can help me get my Logitech diNovo stuff working under Ubuntu...

The problem I have is that I have to unplug the dongle on boot to use the keyboard and mouse, when I plug it back in again everything works except the bluetooth, I think they are working in USB mode.

This is what dmesg displays:

```
[   82.435287] usb 1-6: USB disconnect, address 14
[   82.435290] usb 1-6.1: USB disconnect, address 22
[   82.696822] usb 1-6.2: USB disconnect, address 19
[   82.697015] usb 1-6.3: USB disconnect, address 20
[   84.089480] usb 1-6: new full speed USB device using ohci_hcd and address 23
[   84.300303] usb 1-6: configuration #1 chosen from 1 choice
[   84.303242] hub 1-6:1.0: USB hub found
[   84.306220] hub 1-6:1.0: 3 ports detected
[   84.664221] usb 1-6.2: new full speed USB device using ohci_hcd and address 24
[   84.789297] usb 1-6.2: configuration #1 chosen from 1 choice
[   84.805273] input: Logitech Logitech BT Mini-Receiver as /class/input/input6
[   84.805292] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-6.2
[   85.024220] usb 1-6.3: new full speed USB device using ohci_hcd and address 25
[   85.153301] usb 1-6.3: configuration #1 chosen from 1 choice
[   85.172277] input: Logitech Logitech BT Mini-Receiver as /class/input/input7
[   85.172319] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-6.3

```

I have added the bluetooth devices as the guide suggests but as bluetooth seams to be off I can't actually connect them, I also made the modification to enable at boot, but nothing works unless I unplug/plug back in the dongle.

Any ideas? :)

---

### Post by bubbalouie on 2008-01-25
> **alamarco said:**
> Thanks for the guide. Is there any other way to determine the MAC address of the devices?

Under my mouse and keyboard there are black marks for what I assume is the seriel #'s. My keyboard and mouse are refurbished. These black markings cover part of the BTA section so I'm unable to determine the MAC address in this manner.

edit: Just to let you know, I ended up getting it working with hcitool. I thought I just had to press the Connect button, but instead I had to hold it down for it to be recognized during the searching process.

edit2: Woke up this morning and the devices are no longer connected. When I do a reconnect with 'sudo hidd --search' it doesn't find the devices. Is there anyway to make the connection stay? Both my keyboard and mouse are no longer connected.
Nothing springs to mind sorry, there is a bug that causes the system to kill of bluetooth when the system goes into a low power mode. the following command will reboot the bluetooth service and reconnect the devices:

```
sudo /etc/init.d/bluetooth restart
```

If this makes things reconnect I do have a 'fix' however it is quite ugly (also it is not a total fix, it merely reduces the frequency at which this happens from a few times a day to every few days/weeks), I will post instructions next time I am home (change exists only on my laptop sorry).

---

### Post by bubbalouie on 2008-01-25
> **Philio said:**
> Hi, wondering if anyone can help me get my Logitech diNovo stuff working under Ubuntu...

The problem I have is that I have to unplug the dongle on boot to use the keyboard and mouse, when I plug it back in again everything works except the bluetooth, I think they are working in USB mode.

This is what dmesg displays:

```
[   82.435287] usb 1-6: USB disconnect, address 14
[   82.435290] usb 1-6.1: USB disconnect, address 22
[   82.696822] usb 1-6.2: USB disconnect, address 19
[   82.697015] usb 1-6.3: USB disconnect, address 20
[   84.089480] usb 1-6: new full speed USB device using ohci_hcd and address 23
[   84.300303] usb 1-6: configuration #1 chosen from 1 choice
[   84.303242] hub 1-6:1.0: USB hub found
[   84.306220] hub 1-6:1.0: 3 ports detected
[   84.664221] usb 1-6.2: new full speed USB device using ohci_hcd and address 24
[   84.789297] usb 1-6.2: configuration #1 chosen from 1 choice
[   84.805273] input: Logitech Logitech BT Mini-Receiver as /class/input/input6
[   84.805292] input: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-6.2
[   85.024220] usb 1-6.3: new full speed USB device using ohci_hcd and address 25
[   85.153301] usb 1-6.3: configuration #1 chosen from 1 choice
[   85.172277] input: Logitech Logitech BT Mini-Receiver as /class/input/input7
[   85.172319] input,hiddev96: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:0b.0-6.3

```

I have added the bluetooth devices as the guide suggests but as bluetooth seams to be off I can't actually connect them, I also made the modification to enable at boot, but nothing works unless I unplug/plug back in the dongle.

Any ideas? :)
Perhaps the service tries to launch before the USB deice is fully functional, does restarting the bluetooth service over SSH allow the devices to reconnect?

Sorry, re-read your question, I wouldn't have a clue with that sorry, perhaps USB legacy mode is enables in your BIOS, but sadly I really don't know.

Good luck with it though, hopefully someone more knowledgeable than me can shed a little light on this.

---

### Post by Philio on 2008-01-25
> **bubbalouie said:**
> Perhaps the service tries to launch before the USB deice is fully functional, does restarting the bluetooth service over SSH allow the devices to reconnect?

Sorry, re-read your question, I wouldn't have a clue with that sorry, perhaps USB legacy mode is enables in your BIOS, but sadly I really don't know.

Good luck with it though, hopefully someone more knowledgeable than me can shed a little light on this.

Actually that's a great idea I'll SSH from my laptop and see if I can get it working that way!

---

### Post by Philio on 2008-01-25
Yep, it's working!!! :guitar:
For some reason I wasn't asked for a passkey, but everything is paired now and shows in the Bluetooth Preferences.
Thanks for your help :)

Note: If anyone else is in a similar situation to me and you have no other keyboard/mouse you can plug in to get the bluetooth setup, you can complete the entire guide over SSH and once each device is connected you will then be able to use your computer fine with the bluetooth devices :)

---

### Post by alamarco on 2008-01-25
Thanks for response. I'll give it a try next time this happens. It seems my mouse is now keeping connection, but sometimes the keyboard loses connection and wont connect unless I do the "hidd --search" command while pressing the connect button.

One issue that I have that's more serious. Sometimes I find keystrokes repeat. For example, pressing Alt+Tab while cycle through all windows for a small period of time, I'm talking like maybe 2-5 seconds. When pressing Ctrl+T in Firefox sometimes I will get 10-20 new tabs open which will lag the browser while they open. As you can see, depending on the situation it can become really annoying. Alt+Tab I can deal with, but stuff like Ctrl+T in Firefox is a major issue.

Is there anyway to fix this key repeating issue?

---

### Post by bubbalouie on 2008-01-26
I have experienced the repeating once before, restarting the bluetooth service fixed it right away, when i press win+b a dialog I configured pops up which allows me to give a password so the service can be restarted. To apply my fix I edited the following file:

```
/etc/default/acpi-support
```

There is a line in it that says:

```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""
```

I Changed it to:

```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="hidp rfcomm l2cap bluetooth hci_usb usbcore"
```

It has vastly reduced the incidence of the bluetooth vanishing, though I am not fully certain about why....

There is a bug assosciated with this that has been reported, but not enough people have reported it for anyone to deal with it (fair enough frankly).... Since the last gutsy update I applied the frequency of the problem has gone up again, which I find to be quite annoying, though I can't do much about it.

Good luck

---

### Post by bwtranch on 2008-01-26
Gee, very impressive. I'm at a loss for words (my wife would say "for the first time").

---

### Post by alamarco on 2008-01-26
Ah, I hope they fix this repeating issue somehow. I guess I'm lucky in a way that I'm using my laptop. Whenever the keys start to repeat it seems to stop when I press a key on the laptops keyboard.

Still a PITA though :(

---

### Post by Philio on 2008-01-27
> **bubbalouie said:**
> I have experienced the repeating once before, restarting the bluetooth service fixed it right away, when i press win+b a dialog I configured pops up which allows me to give a password so the service can be restarted. To apply my fix I edited the following file:

```
/etc/default/acpi-support
```

There is a line in it that says:

```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""
```

I Changed it to:

```
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="hidp rfcomm l2cap bluetooth hci_usb usbcore"
```

It has vastly reduced the incidence of the bluetooth vanishing, though I am not fully certain about why....

There is a bug assosciated with this that has been reported, but not enough people have reported it for anyone to deal with it (fair enough frankly).... Since the last gutsy update I applied the frequency of the problem has gone up again, which I find to be quite annoying, though I can't do much about it.

Good luck

I've noticed that sometimes if the computer is idle for a while the bluetooth seams to sleep and the keyboard/mediapad don't always automatically connect again when you hit a button, any idea if this solves this issue?

---

### Post by alamarco on 2008-01-29
I think I have to stay away from keyboard shortcuts for a while. I have Win+E opening nautilus and that wasn't a good time for a repeat to happen. I thought my laptop froze, but after a minute or two it loaded like 50+ nautilus windows.

GG :)

---

### Post by bubbalouie on 2008-01-29
> **Philio said:**
> I've noticed that sometimes if the computer is idle for a while the bluetooth seams to sleep and the keyboard/mediapad don't always automatically connect again when you hit a button, any idea if this solves this issue?
Prior to my last update it did 'resolve' the issue, the updates changed that a little though. I have since found a possible fix, my keyboard has not lost it's connection in a few days now, the mouse will, but only if it left idle for a long time and turning it off and on again fixes it (no restart needed), sadly I messed around with so many lines I can't remember what I changed exactly.

I can however attach the files I changed (I have bolded the lines I remember changing, but it may be more), I don't know if this will help anyone else though, really I wished I could help more, but without spending a few days teaching myself the intricacies of the linux bluetooth system (assuming it is even possible with a feww days effort) I'm afraid this is all I can do.

Anyway, if this helps anyone please let us know, perhaps then we have a fix, if it doesn't help, let us know, save other people the time taken to find out it does nothing :P

Cheers :)

Ryan

Files:
/etc/default/bluetooth 
```
# Defaults for bluez-utils

# This file supersedes /etc/default/bluez-pan.  If
# that exists on your system, you should use this
# file instead and remove the old one.  Until you
# do so, the contents of this file will be ignored.

# start bluetooth on boot?
# compatibility note: If this variable is not found bluetooth will
# start
**BLUETOOTH_ENABLED=1**

############ HIDD
#
# To have Bluetooth mouse and keyboard support, get the
# Linux 2.6.6 patch or better from bluez.org, and set 
# HIDD_ENABLED to 1.
**HIDD_ENABLED=1**
**HIDD_OPTIONS="--connect 00:07:61:33:60:91  --connect 00:07:61:33:3E:8E --connect 00:07:61:33:50:78 --server"**
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

/etc/bluetooth/hcid.conf 
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
	**security auto;**

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	**pairing multi;**

	# Default PIN code for incoming connections
	passkey "1234";
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
	**lm accept;**

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}


device 00:07:61:33:3E:8E {
	name "Logitech diNovo Keyboard";
	auth enable;
	encrypt enable;
}

device 00:07:61:33:50:78 {
	name "Logitech Mediapad";
	auth enable;
	encrypt enable;
}

device 00:07:61:33:60:91 {
	name "Logitech MX1000 mouse"
}

device 00:07:61:3f:f8:cf {
	name "Bluetooth travel mouse"
}

```

/etc/default/acpi-support
```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
**MODULES=""**

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
**STOP_SERVICES="bluetooth"**

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

```

---

### Post by bunkacid on 2008-02-16
I have a Logitech V470.
Here is the pertinent section of my xorg.conf which enables all the buttons.

```
Section "InputDevice"
    Identifier     "4ButtonBluetoothMouse0"
    Driver         "evdev"
    Option         "SendCoreEvents" "true"
    Option         "Protocol" "auto"
    Option         "Name" "Logitech Bluetooth Mouse"
    Option         "ZAxisMapping" "4 5 7 6"
    Option         "ButtonMapping" "1 2 3 7 6 10 11"
    Option         "Resolution" "800"
EndSection

```

---

### Post by Kiwi-Hawk on 2008-07-22
Hi



I'm getting a dialog box:

```

Couldn't display "obex://[00:07:61:98:ec:0c]/".

Error: Host down
Please select another viewer and try again

```

and 

```

Couldn't display "obex://[00:07:61:98:1c:a2]/".

Error: Host down
Please select another viewer and try again

```

when I try to connect to both keyboard ans mouse

any thoughts please

Cheers
Kiwi-Hawk

---

