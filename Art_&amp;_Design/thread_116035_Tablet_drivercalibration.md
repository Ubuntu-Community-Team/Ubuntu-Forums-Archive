---
title: "Tablet driver/calibration"
date: 2006-01-11
forum: Art &amp; Design
---

### Post by genii on 2006-01-11
Anyone know how to get a Jam Studio drawing tablet going? USB connector, model is KG-TAB1
The system sees it but whenever the stylus is placed on the surface the cursor jumps to the top of the screen and seems to gravitate there. Calibration settings somewhere in X possibly?

---

### Post by yabbadabbadont on 2006-02-10
[QUOTE=genii]Anyone know how to get a Jam Studio drawing tablet going? USB connector, model is KG-TAB1
The system sees it but whenever the stylus is placed on the surface the cursor jumps to the top of the screen and seems to gravitate there. Calibration settings somewhere in X possibly?[/QUOTE]

I would like to see a guide for this too.  The kernel module is present in Breezy, but the jamstudio driver doesn't appear to be included in the version of X used by Breezy.  However, I know that the driver is part of the official xorg 6.8.0 (and later) versions.

---

### Post by autocrosser on 2006-03-04
Hi--
I'm running Dapper/Xorg 7.0--There is a input driver for the JamStudio tablet--I am trying to get it to do more than just move the cursor around (cursor works-button is right click). Here is the man page---

**js_x(4) - Linux man page**

     **NAME **

 js_x - JamStudio input driver  **SYNOPSIS **

 **Section "InputDevice"**
**  Identifier "***devname***"**
**  Driver "js_x"**
**  Option "Device"   "***devpath***"**
**  Option "MaxX"  "***int***"**
**  Option "MaxY"  "***int***"**
**  Option "MinX"  "***int***"**
**  Option "MinY"  "***int***"**
**  Option "PressMax"  "***int***"**
**  Option "PressMin"  "***int***"**
**  Option "PressDiv"  "***int***"**
**EndSection**  **DESCRIPTION **

 **js_x** is an Xorg input driver for JamStudio devices. The **js_x** driver functions as a pointer input device, and may be used as the X server's core pointer.  
**SUPPORTED HARDWARE **

 This driver supports the KB-Gear JamStudio pentablet. This X-Input driver should work on any OS supporting the hiddev raw USB HID driver.  **CONFIGURATION DETAILS **

 Please refer to [xorg.conf]("http://www.die.net/doc/linux/man/man5/xorg.conf.5.html")(5x) for general configuration details and for options that can be used with all input drivers. This section only covers configuration details specific to this driver.  **Option** *Device* *path* sets the path to the raw HID device to which the tablet was assigned. This option is mandatory. **Option** *MinX* *int* **Option** *MaxX* *int* **Option** *MinY* *int* **Option** *MaxY* *int* sets the minimum and maximum values returned for the absolute X,Y axis of the pen tablet. These values default to 0-8000 for X and 0-6000 for Y. It should generally be safe to leave these values untouched. **Option** *PressMin* *int* **Option** *PressMax* *int* sets the minimum and maximum values returned for the pressure sensitive tip. These values default to 0-127. It should generally be safe to leave these values untouched. **Option** *PressDiv* *int* sets the divider for the returned pressure value. This option will allow you to return a smaller set of values for the pressure sensitive tip allowing for finer control. The returned value is computed as follows:  *X / PressDiv = returned value* where X equals the value read from the tablet.  **SEE ALSO **

 [xorg]("http://www.die.net/doc/linux/man/man1/xorg.1.html")(1x), [xorg.conf]("http://www.die.net/doc/linux/man/man5/xorg.conf.5.html")(5x), xorgconfig(1x), [xserver]("http://www.die.net/doc/linux/man/man1/xserver.1.html")(1x), [x]("http://www.die.net/doc/linux/man/man7/x.7.html")(7x).

Had two failures so far--(x-server non-start)-will report back if I get the tablet to do what the driver said it can do----

---

### Post by Silentheero on 2007-05-13
I am also trying to install this jam studio pad (actually it is the Pablo Internet Tablet but the driver is the same) with no success. I am running feisty. I have the windows drivers and it works on my notebook in windows but not in ubuntu. I have not worked with X much so I am not sure how to configure it. The xorg.conf contains this about the input devices 
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection
```

I installed the package "xserver-xorg-input-jamstudio" on the Synaptic Package Manager but I cant find the drivers or the files to replace the "device" option above. I have looked at the wacom installation and tried to copy it with jamstudio, but wont work. If anyone has gotten it to work, please post your input portion of xorg.conf and how to get the drivers in the /dev/input/ folder.

Sites I have been looking at:
[http://www.die.net/doc/linux/man/man4/js_x.4.html](http://www.die.net/doc/linux/man/man4/js_x.4.html)
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
[http://www.amazon.com/KB-Gear-KG-TAB1-Jam-Studio/dp/B000050AVT](http://www.amazon.com/KB-Gear-KG-TAB1-Jam-Studio/dp/B000050AVT)

---

### Post by Silentheero on 2007-05-14
Bump

---

### Post by yabbadabbadont on 2007-05-16
man js_x  should tell you how to configure it.  You may have to add kbtab to /etc/modules so that the kernel module will be loaded during boot.

---

### Post by Silentheero on 2007-05-20
I have read the man page on it and it doesn't help much, because I don't know how to configure it. I read another post from someone who was able to use the pad on 6.10 with no setup here [http://www.linuxforums.org/forum/peripherals-hardware/75627-js_x-kb-gear-jam-studio-pablo-graphix-tablet-drivers.html]("http://www.linuxforums.org/forum/peripherals-hardware/75627-js_x-kb-gear-jam-studio-pablo-graphix-tablet-drivers.html")

This guy has tried to write a driver for it but it is old and I wouldn't know where to start to try to compile and test it. [http://lwn.net/Articles/13740/]("http://lwn.net/Articles/13740/")

I can plug it in and it shows "KBGear USB Tablet" under the Device Manager, but under the device tab the vendor, device type and capabilities show "unknown". 

I would just like some confirmation that someone else is using this on feisty and how they got it to work. Again, thanks for any help.

---

### Post by yabbadabbadont on 2007-05-21
OK, I have the Pablo Internet Edition tablet, Model KG-PB20.  When plugged in, a new hid device is created for it.  I verified that it was the correct device by "cat'ing" it and then moving the stylus across the tablet and watching the garbage being output.  The kbtab module is the kernel module that needs to be loaded, however it does not recognize this device.  I remember running into this a few years ago when I was running Gentoo.  I had to hack the module source and add the specific device id for this tablet to the list of device id's that were already there.  Once I had done that (and rebuilt the module of course) my tablet was recognized.  However, at that time, there wasn't an X driver for the tablet so it could only be used as a second mouse...  which is why I quit messing with it then.  I apologize for not remembering this when you posted earlier.  Now I just have to figure out how to install the kernel sources and find the proper way to build a custom module.  It will probably be this weekend before I can get to it though.  I may just end up building a fully custom kernel (like I always did with Gentoo) and dump the whole initrd completely.

---

### Post by Silentheero on 2007-05-21
Awesome, thanks a lot. No rush please. I am not in a hurry, but it would be nice to be use this tablet.

There seems to be an X driver for the tablet now, "xserver-xorg-input-jamstudio" on the Synaptic Package Manager, but I do not have enough experience to figure out what to do with that information or to know if it even works. I just moved started to use ubuntu exclusively about two months ago and have been slowly working on projects on it one at a time. This is the one i'm stuck on right now. ](*,):)

---

### Post by yabbadabbadont on 2007-05-21
One of the things that I need to know to modify the kbtab module is the lsusb output from when your tablet is plugged in.  Mine shows ```
ID 084e:1002 KB Gear Pablo Tablet
```  The driver as shipped with Ubuntu only works with ```
084e:1001
```  I've added my product ID (1002) to the list of valid devices and am in the process of rebuilding the linux-image-2.6.20-15-generic kernel.  (It takes a while as pretty much everything is enabled in the kernel config as modules...)

---

### Post by yabbadabbadont on 2007-05-21
Well, that was a wasted couple of hours...  It appears that the tablet is claimed by the usbhid module and it is creating the raw hid device (/dev/hiddev1 in my case).  Simply configuring the js_x X driver to use /dev/hiddev1 resulted in the tablet acting as a second mouse with one button (the tip).  (it ignores the side button on the pen)  As a test, I booted back into the default linux-generic kernel and it still worked.  I have no clue why the kbtab module even exists anymore if usbhid handles it.  Here are the changes that I made to xorg.conf to get it to work.  (I haven't tried messing with configuring it in GIMP or similar yet)
```
Section "InputDevice"
        Driver          "js_x"
        Identifier      "stylus"
        Option          "Device"        "/dev/hiddev1"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
EndSection

```
You will probably need to mess with the tip pressure options (PressMax, PressMin, PressDiv) as I found the default sensitivity to be way too sensitive.  The lightest pressure on the tip resulted in numerous mouse clicks.  (When I clicked on my firefox icon, it launched 10 copies of it... :lol:)

---

### Post by Silentheero on 2007-05-24
Looks like the info i am getting from mine when plugged in is

linux.device_file     /dev/hiddev0

usb_device.product           KBGear USB Tablet
usb_device.product_id      4098 (0x1002)


It is recognising it as a KBGear Tablet instead of a Pablo (which I have). I am gonna try to config the js_x and see what happens.

Edit:

Cool! I am getting a response from it now! I got the pad to work and the first click (the pen end) working and the sensitivity is great at default for me. 
Here is what I put into the xorg.conf:

```
Section "InputDevice"
	Driver		"js_x"
	Identifier	"stylus"
	Option		"Device"	"/dev/hiddev0"
	Option		"Type"		"stylus"
EndSection

Section "InputDevice"
	Driver		"js_x"
	Identifier	"eraser"
	Option		"Device"	"/dev/hiddev0"
	Option		"Type"		"eraser"
EndSection

Section "InputDevice"
	Driver		"js_x"
	Identifier	"cursor"
	Option		"Device"	"/dev/hiddev0"
	Option		"Type"		"cursor"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

But as you said, I cant get the secondary click on the side to work, but I am ecstatic that I got this far!

EDIT:
Err, strike that sensitivity comment. It is a little too sensitive, i'll mess with that and see what I can do about lowering that. 

The reason there are three entries in the xorg.conf is because when I first plugged the pad in it created those three entries. So i just edited them to the js_x driver. I dont know what they do or if they are necessary.

---

### Post by yabbadabbadont on 2007-05-25
The man page for the js_x driver doesn't list any "Type" options that can be used with it.  Of course, it wouldn't be the first time that the man page didn't match reality...  ;)

---

### Post by Silentheero on 2007-05-27
Ok, I had unplugged the tablet, then later suspended. When I cut it back on, x wouldnt start. I had to replace the config file with the back (that I am glad I made). Dunno what happened but I am having problems with nautilus when coming back from suspension. (I think that is what it is called... the graphical folder browser).

---

### Post by gruvsyco on 2007-05-27
[this]("http://alexmac.cc/tablet-apps/") might be of use.

---

### Post by jhnphm on 2007-12-06
Thread necro, but it seems to use the usbhid instead of the kbtab driver since it doesn't recognize the device ID, and therefore ignores the side button.

This fixes it

```
diff -uprN linux-source-2.6.22/drivers/hid/usbhid/hid-quirks.c linux-source-2.6.22-mod/drivers/hid/usbhid/hid-quirks.c
--- linux-source-2.6.22/drivers/hid/usbhid/hid-quirks.c 2007-10-14 18:33:09.000000000 -0400
+++ linux-source-2.6.22-mod/drivers/hid/usbhid/hid-quirks.c     2007-12-06 04:09:13.000000000 -0500
@@ -179,6 +179,7 @@
 
 #define USB_VENDOR_ID_KBGEAR           0x084e
 #define USB_DEVICE_ID_KBGEAR_JAMSTUDIO 0x1001
+#define USB_DEVICE_ID_KBGEAR_PABLO     0x1002
 
 #define USB_VENDOR_ID_LD               0x0f11
 #define USB_DEVICE_ID_LD_CASSY         0x1000
@@ -368,6 +369,7 @@ static const struct hid_blacklist {
        { USB_VENDOR_ID_GTCO, USB_DEVICE_ID_GTCO_1006, HID_QUIRK_IGNORE },
        { USB_VENDOR_ID_IMATION, USB_DEVICE_ID_DISC_STAKKA, HID_QUIRK_IGNORE },
        { USB_VENDOR_ID_KBGEAR, USB_DEVICE_ID_KBGEAR_JAMSTUDIO, HID_QUIRK_IGNORE },
+       { USB_VENDOR_ID_KBGEAR, USB_DEVICE_ID_KBGEAR_PABLO, HID_QUIRK_IGNORE },
        { USB_VENDOR_ID_LD, USB_DEVICE_ID_LD_CASSY, HID_QUIRK_IGNORE },
        { USB_VENDOR_ID_LD, USB_DEVICE_ID_LD_POCKETCASSY, HID_QUIRK_IGNORE },
        { USB_VENDOR_ID_LD, USB_DEVICE_ID_LD_MOBILECASSY, HID_QUIRK_IGNORE },
diff -uprN linux-source-2.6.22/drivers/input/tablet/kbtab.c linux-source-2.6.22-mod/drivers/input/tablet/kbtab.c
--- linux-source-2.6.22/drivers/input/tablet/kbtab.c    2007-07-08 19:32:17.000000000 -0400
+++ linux-source-2.6.22-mod/drivers/input/tablet/kbtab.c        2007-12-06 04:17:40.000000000 -0500
@@ -93,6 +93,7 @@ static void kbtab_irq(struct urb *urb)
 
 static struct usb_device_id kbtab_ids[] = {
        { USB_DEVICE(USB_VENDOR_ID_KBGEAR, 0x1001), .driver_info = 0 },
+       { USB_DEVICE(USB_VENDOR_ID_KBGEAR, 0x1002), .driver_info = 0 },
        { }
 };


```

---

### Post by jhnphm on 2007-12-06
Nevermind, applying the patch allows you to use the button, but it kills pressure sensitivity since you have to use the mouse driver with it. 

[http://www.obsidianrook.com/pile/svlug-hints_about_possible_problems_with_usb_modules_conflicting_with_each_other.html](http://www.obsidianrook.com/pile/svlug-hints_about_possible_problems_with_usb_modules_conflicting_with_each_other.html)

---

