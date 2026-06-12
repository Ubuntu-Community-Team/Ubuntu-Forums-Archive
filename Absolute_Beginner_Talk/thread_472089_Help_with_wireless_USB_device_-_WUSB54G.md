---
title: "Help with wireless USB device - WUSB54G"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Sconts on 2007-06-12
I have an AMD64 x2 4800+ processor
and Kubuntu Feisty.

I have installed ndiswrapper, and properly installed the wusb54g.inf driver file.  
When I enter ```
ndiswrapper -l
```

I get

```
wusb209x.sys : invalid driver!
wusb20xp.sys : invalid driver!
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save.2: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save.3: Permission denied
WARNING: Failed to open config file /etc/modprobe.d/blacklist.save.1: Permission denied
wusb54g : driver installed
        device (5041:2235) present (alternate driver: prism54usb)

```

From what I have read on these forums and various other forums, it seems that all I need is for the .inf file to work...and according to this, it does.  However my device is still not recognized.  Any ideas?
Thanks

EDIT: Forgot to add, when i do "lsusb", it confirms that 5041:2235 is the linksys device. Here's the exact result: ```
Bus 001 Device 002: ID 5041:2235 Linksys (?)
```
(yes, it had the '(?)' in the actual code)

---

### Post by Sconts on 2007-06-12
I have also tried several different versions of the .sys files, yet I can never get them to work.  I have been following several guides and trying everything I possibly can, yet I cannot get them to install.  

As for the .inf file, I'm glad it installed correctly and Ubuntu recognizes it as being for the WUSB54G...I just don't understand why there is nothing anywhere to allow me to connect with it.

---

### Post by ugm6hr on 2007-06-12
1.
      Card: Linksys WUSB54Gv1, 802.11b/g, USB 2.0

    *
      Chipset: Prism54
    *
      usbid: 5041:2234
    *
      Driver: Linksys Windows XP driver [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp)
    *
      Other: Works smoothly, of course ;) - this is the device the USB extension was originally developed for. WEP is running, WPA is supported using wpa_supplicant 0.2.5. No problems with both 1.1 and 2.0 host controllers. As with many other USB devices, no success with 2.4 kernels so far. Try to use 2.6.7 or better. There is a native driver for Prism54 that is working on USB support. View its status at Prism54.org
    *
      Other: Works with latest Windows Driver from linksys.com. No success with 2.4 kernels (even with 8k stack). Works with kernel 2.6.11 and 2.6.12. Works smoothly with 2.6.12 and ndiswrapper 1.14.
    *
      Other: Driver from Linksys is old. Alternate driver for Sitecom WL-125 driver at [http://www.sitecom.com/showdownload.php?id=1998](http://www.sitecom.com/showdownload.php?id=1998) is newer version. With this, the card doesn&#8217;t disconnect. Tested with card with usbid 1915:2234.

From ndiswrapper wiki:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)

Hope that helps.

EDIT: Not sure if the prism native driver is interefering - try blacklisting it in /etc/modprobe.d/blacklist (I think you can just add the line "blacklist prism54usb")

---

### Post by Sconts on 2007-06-12
Thanks, but no luck yet.
I had tried those more recent drivers before and they didn't work either.
=/

---

### Post by wreti on 2007-06-12
Is it possible that you have a WUSB54Gv1 driver installed but a WUSB54Gv4 device? I had this same problem once only to find out that the version 1, 2 and 3 devices were easily compatible between drivers but the version 4 devices required their own specific drivers and were a little less friendly with Ubuntu.

---

