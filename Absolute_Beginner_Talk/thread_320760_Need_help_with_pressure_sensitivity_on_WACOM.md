---
title: "Need help with pressure sensitivity on WACOM"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by Jack the R on 2006-12-17
That was surprisingly easy.  

Now - how does one make the pressure sensitivity work on the Wacom?

---

### Post by Littleweseth on 2006-12-17
IIRC, when i plugged in my Wacom it loaded the appropriate driver and handled pressure sensitiviy perfectly (in GIMP at least.) Is it actually not working for you?

---

### Post by Jack the R on 2006-12-17
This looks helpful - 

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by Jack the R on 2006-12-17
Clicking on Preferences>Input Devices>Extended Input Devices>Configure Extended Input Devices gives the error message "No Extended Input Device."  Yet the tablet is able to position the cursor.

---

### Post by Jack the R on 2006-12-18
Another useful item - testing the tablet:

[http://linuxwacom.sourceforge.net/index.php/howto/testtablet](http://linuxwacom.sourceforge.net/index.php/howto/testtablet)

Looks like I don't have the Wacom driver installed.

---

### Post by Littleweseth on 2006-12-18
[https://help.ubuntu.com/community/Install_linuxwacom_driver](https://help.ubuntu.com/community/Install_linuxwacom_driver)

Have fun. :)

---

### Post by Jack the R on 2006-12-18
Oops, I see there's a different test for 2.4 and 2.6 kernels.  

Which kernel does 6.10 use?  2.6?

I'm guessing it's 2.6.

Running more /proc/bus/input/devices this time gives me both the 056A vendor code and N: Name="Wacom Graphire"

Running tail -f /var/log/messages gives this result: 

usb 3-1: new low speed usb device using usb uhci_hcd and address 4
usb 3-1: configuration #1 chosen from 1 choice
input: Wacom Graphire as /class/input/input5

That doesn't look like the lines you can't have (see the bottom of the tablet detection page).  It appears that Ubuntu is detecting the Wacom fine and the driver is installed.

On to the next step tomorrow . . .



Littleweseth - nope, no pressure sensitivity for me.

---

### Post by Littleweseth on 2006-12-18
hmm.

Going out on a limb here; let's find out if the wacom driver is loaded.
Go to a terminal and type 'lshw' (list hardware - akin to 'ls' for listing files, except it lists every damn piece of hardware attached to your computer.)

Under 'usb' somewhere (it's an exhaustive long list) you should see something like

*-usb:0
description: Mouse
product: CTE-630-UV3.1-4
vendor: WACOM
physical id: 1
bus info: usb@1:1
version: 3.14
capabilities: usb-1.01
configuration: driver=wacom maxpower=40mA speed=1.5MB/s

As i understand it, the last line is the important bit. If you see 'driver=wacom' there, you're set. If not, that may be the problem.

I also did a 'lsmod | grep wacom', bringing up

wacom   15232    0
usbcore   130820    4 wacom,usbhid,uhci_hcd

I have no idea what this means, but i presume seeing 'wacom' in the right column is a Good Thing.

---

### Post by Jack the R on 2006-12-18
I'm in good shape on both counts.

---

### Post by Littleweseth on 2006-12-18
I'm outta ideas :) I'm no expert though, just a clued-up noob.

Just quickly - are you sure that it's not a hardware fault? I know that Wacom pens are rather delicate things - the eraser end on mine has completely ceased to function, for example. Plug it into some other computer?

---

### Post by Jack the R on 2006-12-18
It works fine in Windows, on the same machine.

---

### Post by Jack the R on 2006-12-18
Viewing the Raw Data:

[http://linuxwacom.sourceforge.net/index.php/howto/viewdata](http://linuxwacom.sourceforge.net/index.php/howto/viewdata)

I've got no activity on event0 or event 1, mouse-only activity on event 2, mouse activity on mouse0, and wacom activity on mouse 1.  

/sbin/rmmod wacom gives me "no such directory"

Thoughts?

---

### Post by xscd on 2006-12-18
> **Jack the R said:**
> That was surprisingly easy.  

Now - how does one make the pressure sensitivity work on the Wacom?

Make sure you have both the kernel driver (wacom.ko, which merely reads (but doesn't understand or interpret to any great extent) the data from the tablet and makes it accessible and available to other programs), and the Xorg GUI driver (wacom_drv.o, which allows Xorg to read and interpret the tablet data supplied by the kernel driver and to make it actually **DO** something, like vary the stroke width of the paintbrush in the Gimp in response to pressure on the stylus.

To see if you have both of these, update the locate program's database with:

sudo updatedb

Then try to locate both files:

locate wacom.ko
(this is the kernel Wacom driver,  in /lib/modules/2.6.17-10-386/kernel/drivers/usb/input/wacom.ko in my Edgy Eft installation)

locate wacom_drv.o
(this is Xorg's Wacom driver for the GUI environment (Gnome, KDE, Fluxbox, whatever); it should probably be in /usr/lib/xorg/modules/input/wacom_drv.o)

An easy way to make sure all of this is installed, plus a udev script to automatically create the device /dev/input/wacom whenever the tablet is plugged into a USB port, is to use synaptic to install the following 3 packages:
[list]
[*]wacom-tools (this installs the udev script and rules)
[*]xserver-xorg-input-wacom (this installs the wacom_drv.o Xorg GUI driver)
[*]wacom-kernel-source (this will install the kernel driver, wacom.ko, but it is probably already installed (check and see), and remember that to install this package you will need to first install at least the kernel headers package for the version of the kernel you are using, in order for this package to configure itself with and install properly)
[/list]

The last one (wacom-kernel-source, which installs the wacom.ko kernel driver) you probably don't need to install because it is probably already installed.

Be sure to check your /etc/X11/xorg.conf file to make sure that there are at least InputDevice entries for the Wacom stylus and eraser.

Best wishes,
:)

---

### Post by Jack the R on 2006-12-19
sudo updatedb didn't do anything (or at least no results were displayed in the terminal window).  I'm assuming it's a legitimate command since "command not found" wasn't displayed afterwards.  Any ideas?

---

### Post by xscd on 2006-12-19
> **Jack the R said:**
> sudo updatedb didn't do anything (or at least no results were displayed in the terminal window).  I'm assuming it's a legitimate command since "command not found" wasn't displayed afterwards.  Any ideas?

Yes-- If you don't know what a command does, look at the manual page for the command:

man updatedb

To see if a command is installed on your system, type in a terminal window:

which (command), like this:

which updatedb
-or-
whereis updatedb

updatedb is the command to update the database for the "locate" command. updatedb catalogs all of the directory and file names on mounted disks so that locate can find them in that database, rather than doing a lengthy search of your hard disks. That's why the locate command is so fast. So--

sudo updatedb

will update the locate database. Then--

locate wacom.ko
-or--
locate wacom_drv.o

will tell you the current location of those two files, if they exist on your system.

---

### Post by Jack the R on 2006-12-19
Ahhh, that makes sense!  No wacom_drv.o, wacom.ko found in lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/wacom.ko

What's next :)

---

### Post by Jack the R on 2006-12-20
Found 3 lines in sections of xorg.conf like so - 
> 
option "Device"  "/dev/wacom"   #change to "/dev/input/event" for usb.

I made the changes and overwrote the version of xorg.conf in /etc/X11, then  rebooted the machine.

But, when I went to set "Extended Input Devices," in GIMP it still said "No Extended Input Devices."

---

### Post by xscd on 2006-12-20
> **Jack the R said:**
> Found 3 lines in sections of xorg.conf like so - 
I made the changes and overwrote the version of xorg.conf in /etc/X11, then  rebooted the machine.
But, when I went to set "Extended Input Devices," in GIMP it still said "No Extended Input Devices."

First, you now know that you have the kernel driver for the 2.6 series Linux kernels installed: wacom.ko

That's great. Now your kernel can see the hardware (the Wacom tablet) and can read the data coming from the tablet.

Now you need to make sure that Xorg (which is responsible for the GUI, like Gnome or KDE) has **its** Wacom driver, in order to read the data that the Linux **kernel** is making available. The Xorg driver **doesn't** read data directly from the tablet. It is the kernel's job to interface with all the hardware on your computer, and other programs must ask or depend upon the kernel to read or write any data to and from any hardware device. To install the Xorg Wacom driver, use synaptic and use the search feature to find packages with "wacom" in the name. When you find those, install the one that is named: xserver-xorg-input-wacom

That package will install the Xorg Wacom driver, wacom_drv.o

So, when you have BOTH the kernel Wacom driver and the Xorg Wacom driver installed, you are almost there!

The next thing to do is to let Xorg know which device file has been selected in the /dev/ directory to represent the Wacom tablet. There are numerous ways to do this, but the **easiest**, with the least amount of knowledge necessary for Linux beginners, is to install the "wacom-tools" package, again using the program synaptic. Wacom-tools will give the real device file, whatever it may happen to be at the time, a nickname of /dev/input/wacom, and **that's** the /dev entry you need to use in your xorg.conf file under the InputDevice sections that pertain to the Wacom tablet, despite what the file itself tells you. So after you install wacom-tools, change /dev/input/event or /dev/wacom to /dev/input/wacom and save the xorg.conf file (be sure to use a plain text editor to edit xorg.conf, **not** a word processor.

So, now you have the kernel driver that can see the Wacom tablet and read its data and make its data available through the use of a "device file" in the /dev/ directory. AND you have the Xorg Wacom driver that can read the data from that device file and interpret that data for use in Gnome, KDE, the Gimp, Inkscape, etc. AND you have installed wacom-tools so that the device file Xorg needs to read will always be called /dev/input/wacom, AND you have edited the xorg.conf file so that the InputDevice sections that are pertinent to the Wacom tablet all have /dev/input/wacom listed in their options.

Then reboot the computer.

Now, after all that, there is only one thing to remember. Xorg reads its configuration file **only** when it starts up. So if you plug in your Wacom tablet **after** Xorg has already started and you are at the GDM login screen or have already logged into Gnome or KDE, you will have to restart Xorg in order for it to re-read its configuration file, xorg.conf. To do that, log out of KDE or GNOME, then press CONTROL-ALT-BACKSPACE to forcibly restart the X server (Xorg).

Now you have the Linux kernel seeing the data from the Wacom tablet and sending that data directly to a file in the /dev directory (/dev/input/wacom). AND you have told Xorg (via its configuration file, xorg.conf) to find that file in the /dev directory (/dev/input/wacom) and read whatever data it can from it. So **now**, after all of that, you can launch the Gimp or Inkscape and set the Wacom tablet as an extended input device.

If that doesn't work, then please re-read this entire thread carefully to see if you may have missed or misinterpreted some of the information. In addition, use UbuntuForums search feature to search for the word "wacom" and read other discussion threads about this same issue.

Rest assured that it can be accomplished because I have a Wacom Intuos3 6x11 widescreen-version tablet that I'm using right now with my Ubuntu Linux Edgy Eft installation. I got it working by doing exactly what I have described in my replies, and it works very well in the GUI (Gnome) as well as in Gimp and in Inkscape (a vector drawing program like Adobe Illustrator).

Good luck!
:)

---

### Post by Jack the R on 2006-12-20
Thanks for taking the time to write all that.  

I'll try it once I get my modem working (doing all this on another machine).

---

### Post by Littleweseth on 2006-12-21
xscd : legendary post. If there isn't a howto already posted, you should write one :)

---

### Post by Scunizi on 2006-12-21
I've got a new Wacom 4x5 and got it working.  I installed 
> sudo apt-get install xserver-xorg-input-wacom wacom-tools

And that didn't take care of everything. I then made changes to xorg. Here's my xorg.

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event2"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
 # Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event2"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
 # Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event2"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
 # Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


You'll notice the missing # marks in the Wacom section and the changes I've made to the location of the /dev/input/event(number).  You have to guess at the event number to make it work and be recognized in Gimp under Config. Input Devices.  Restart GDM after saving the file to see if you got it right (CTRL-ALT-Backspace).  Once you get the event number right Gimp will recognize it with no problem and work correctly.  Configure the stylus, eraser and other option to "Screen" not "Window" for easier and more predictable use. 

The problem I'm still having is maintaining a consistant event number.  If I've got a usb flash drive plugged in the event number changes so I have to go back into xorg and make an event number change.

If anyone knows a solution to that one I'd love to hear it!:D

---

### Post by Scunizi on 2006-12-21
Sorry for the double post.  It's easier to see the fix I did to make it work consistantly.  I removed the # mark in front of the lines that are labeled with #Tablet PC Only and I changed /dev/input/event(number) to /dev/input/wacom.  Restarted GDM and viola!  Working fine.  You do have to play the the menu choices in Gimp to get pressure sensitivity working the way you want.

---

