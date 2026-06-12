---
title: "iBook WiFi options"
date: 2004-11-21
forum: Apple PPC Users
---

### Post by Rincewind on 2004-11-21
Hi,

Ok, so I'm using and enjoying Ubuntu on my PC and I'm planning on replacing OS X on my G4 iBook also.

I have an Airport Extreme card in the iBook already, but as everybody knows by now (hopefully!) this isn't supported due to Broadcom not being able to release drivers.

So has anyone another tried and tested method of WiFi on iBook/Powerbook that Ubuntu will work with no problems? Preferably 802.11g rather than 802.11b (guess
the regular airport card will work).

Thanks,
Chris

---

### Post by osunix on 2004-11-21
I wish I knew a way. Not having the AE driver is the one thing keeping me from running Ubuntu full time on my iBook too.

---

### Post by Rincewind on 2004-11-21
Hi,

I guess I should be more clear:

I'm willing to chuck the AE and use anything else that works!
i.e. USB2 WiFi adapter or another PCMCIA card that will fit under the keyboard (if it exists!).

Chris.

---

### Post by paulproteus on 2004-11-21
I'm using the cheap Syntax USB-400 802.11b wireless stick.

Pros: It's cheap!  Ten bucks on ebay.  And it's white, which is fairly important with this iBook. ;-)  And b is fast enough at 11 Mbps.

Cons: Its drivers (prism2-usb), while loaded by Ubuntu, are not capable of using the "Network configuration management" box in the Computer menu.  That's because they use the linux-wlan-ng configuration system, which Ubuntu does not yet support.  I have scripts to do it manually, which I'd be happy to share.  And it's not 11g.

Advice: Buy something that is not linux-wlan-ng, or work with me on patching Ubuntu's configurator (I'm halfway there...) to work with this driver set.

---

### Post by slux on 2004-11-22
Sorry, the regular Airport card won't work on a new iBook G4 either, you can't fit it in a newer iBook AFAIK.

---

### Post by Rincewind on 2004-11-22
Thanks for the suggestions.

In the end I think I'm going to get something like this:

[http://usa.asus.com/products/communication/wireless/wl-330g/overview.htm](http://usa.asus.com/products/communication/wireless/wl-330g/overview.htm)

There's no need to mess with any drivers at all for that, downside is carrying the little box around with the iBook.

Thanks,
Chris

---

### Post by sparkx on 2004-11-23
Slux is correct. The old Airport card won't work in the new iBook. I had to buy an AE card when I went from a G3 500 to a G4 1GHz.

---

### Post by nyqo on 2004-11-24
So what does one need to do to get a D-Link DWL-122 to work on an iBook G3-700 (running hoary).   I have installed linux-wlan-ng from universe, but I read that the config utility is not compatable with this method.  

1. Should the USB adapter be automatically detected or do I need to run specific commands to enable it?  

2. Can linux-wlan-ng utilize the signal strength applet on the upper tool bar?

---

### Post by nyqo on 2004-11-24
Just got my DWL-122 working on an iBook. In case anyone is interested, I installed the linux-wlan-ng from universe, modified /etc/wlan/wlan.conf and copied /etc/wlan/wlancfg-DEFAULT to /etc/wlan/wlancfg-myssid and edited that accordingly. I then created the following script to run whenever I need it:


#!/bin/sh

sudo modprobe prism2_usb
sudo rmmod prism2_usb
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="myssid" authtype=opensystem
sudo dhclient wlan0

I am up and running. Thanks for all of your help and I hope this can help others.

---

### Post by cvalstad on 2005-03-17
Im working on installing thelinux-wlan-ng drivers but I am stuck at the moment. i have a powerbook g4 with the 5.04 preview version.

this is the error I get:

Build Prism2.5 USB (_usb) driver? (y/n) [n]: y

Linux source directory [/usr/src/linux]:
Linux source tree /usr/src/linux is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed

make: *** [config] Error 1

What do I need to do?

---

### Post by skabber on 2005-03-17
[QUOTE=Rincewind]Thanks for the suggestions.

In the end I think I'm going to get something like this:

[http://usa.asus.com/products/communication/wireless/wl-330g/overview.htm](http://usa.asus.com/products/communication/wireless/wl-330g/overview.htm)

There's no need to mess with any drivers at all for that, downside is carrying the little box around with the iBook.

Thanks,
Chris[/QUOTE]


Does anyone know any more info about devices such as this.  Such as does this need an external power source.  If so that would suck to try and use on the road.  Having to plug in this little router while my laptop is running of batter.

---

### Post by Rincewind on 2005-03-27
[QUOTE=skabber]Does anyone know any more info about devices such as this.  Such as does this need an external power source.  If so that would suck to try and use on the road.  Having to plug in this little router while my laptop is running of batter.[/QUOTE]

It comes with a little cable that plugs in the USB port and draws power from that.  Also comes with a short ethernet cable so it's quite tidy.

Rincewind

---

### Post by chascon on 2005-04-18
Yeah I got a syntax dongle model usb-400 using linux-wlan-ng.
We first got it working at school with hoary, but sinse then I haven't  been able to make it work either here at home or at school.
We had to download and builld to the kernel sources.
Apparently mandrake come with support built in, see
[http://www.mandrakeusers.org/index.php?showtopic=12400](http://www.mandrakeusers.org/index.php?showtopic=12400)

If you still want to make it work:
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=158379&perpage=15&pagenumber=2](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=158379&perpage=15&pagenumber=2)
It has some recommendations on how to make it work with hotplug functionality.  I don't think this is my problem as dmesg sees my dongle when I plug it in.

The README at [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/README)
is vertually useless.

---

### Post by chascon on 2005-04-18
[QUOTE=][/QUOTE]
 If you like I thru up some notes at on getting the syntax usb-400 with hoary and on an early  2004 ibook:
[http://ubuntuppc.webplazahosting.com/index.php](http://ubuntuppc.webplazahosting.com/index.php)

It incomplete but a start.

---

### Post by slux on 2005-04-21
For those looking for something to match their iBook's looks ( I'm guessing a few mac people might, I know I was) :P, check out the[Buffalo Airstation WLI-USB-KB11](http://www.buffalotech.co.uk/webcontent/products/wireless/index.php?cat=11M&itemID=wli-usb-kb11). It works with the prism2_usb driver from linux-wlan-ng and the only drawback is that it's 802.11b. The colour matches an iBook pretty perfectly. There's also a 802.11g version but I think it isn't supported. Isn't the only completely free driver for 802.11g the Prism54? Anyone know of a USB device using that?

This one's Linux only though, no drivers for OS X if someone's looking for a suitable one for a dual boot setup.

---

### Post by Castaa on 2005-04-21
Is anyone here running a standard Airport card with encryption.  I haven't been able to get it to accept the password or the 128 bit key.

---

### Post by comforteagle on 2005-05-10
[QUOTE=nyqo]Just got my DWL-122 working on an iBook. In case anyone is interested, I installed the linux-wlan-ng from universe, modified /etc/wlan/wlan.conf and copied /etc/wlan/wlancfg-DEFAULT to /etc/wlan/wlancfg-myssid and edited that accordingly. I then created the following script to run whenever I need it:


#!/bin/sh

sudo modprobe prism2_usb
sudo rmmod prism2_usb
sudo modprobe prism2_usb prism2_doreset=1
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_autojoin ssid="myssid" authtype=opensystem
sudo dhclient wlan0

I am up and running. Thanks for all of your help and I hope this can help others.[/QUOTE]

When I input "sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable" I get "wlanctl-ng: No such device"

Help?  I just bought the d-link dwl132 -not- 122 as above.

---

### Post by t3h on 2005-06-04
[QUOTE=paulproteus]I'm using the cheap Syntax USB-400 802.11b wireless stick.

Pros: It's cheap!  Ten bucks on ebay.  And it's white, which is fairly important with this iBook. ;-)  And b is fast enough at 11 Mbps.

Cons: Its drivers (prism2-usb), while loaded by Ubuntu, are not capable of using the "Network configuration management" box in the Computer menu.  That's because they use the linux-wlan-ng configuration system, which Ubuntu does not yet support.  I have scripts to do it manually, which I'd be happy to share.  And it's not 11g.

Advice: Buy something that is not linux-wlan-ng, or work with me on patching Ubuntu's configurator (I'm halfway there...) to work with this driver set.[/QUOTE]

Where do you get these things on eBay? I have tried searching for them quite a bit and haven't seen any yet...

I'd like to get one that I can use with my new PB G4 with KisMAC and my old powerbook G3 with Ubuntu on it.

---

### Post by xghstst0riesx on 2005-10-30
[QUOTE=cvalstad]Im working on installing thelinux-wlan-ng drivers but I am stuck at the moment. i have a powerbook g4 with the 5.04 preview version.

this is the error I get:

Build Prism2.5 USB (_usb) driver? (y/n) [n]: y

Linux source directory [/usr/src/linux]:
Linux source tree /usr/src/linux is incomplete or missing!
    See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed

make: *** [config] Error 1

What do I need to do?[/QUOTE]
I had the same problem. Anyone know how to fix this?

---

### Post by pauljwells on 2005-11-01
For anyone based in the UK (and probably elsewhere as it is from a US company) The TrendNet TEW-229UB 801.11b USB dongle got me wifi connection with WEP on BOTH my G4 powerbook and my PC (both running breezy) with no hassle at all. They stock these things at B&Q with all the cables and stuff! In both installs it just showed up (hotplugged) in the network utility. I just had to type in the ESSID and the WEP key and I was connected! The only 'clever' thing I did was to add the config to /etc/network/interfaces so I didn't have to type the WEP key at each reboot.    Setting the wlan0 to auto didn't seem to work and threw up an error about over-current on the usb port. I can post my interfaces file if anyone wants. I couldn't get Network-manager to work with it, which is a shame as this looked really a nice little applet.

---

