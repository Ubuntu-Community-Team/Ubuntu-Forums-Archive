---
title: "Wireless Internet Connection Setup"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by kittykatmeowmeow on 2008-02-17
I just installed UBUNTU 7.1 onto my Sony Vaio Laptop and it is not recognizing a WIFI connection.  When I plug the CAT 6 cable into the wireless router it connects.  How do I get it to recognize my SSID?

---

### Post by Presto123 on 2008-02-17
Do this: be connected to the internet with your network cable, go into System/Administration/Restricted Drivers Manager and the wireless card should show up. If it shows up, click on the box to enable it. A new window will pop up to prompt you for a driver; click on the second option to download from the Internet.

---

### Post by kittykatmeowmeow on 2008-02-17
I followed those instructions exactly and there was only one driver that showed up...and it was checked in use. Any other options??:confused:

---

### Post by Presto123 on 2008-02-17
What is the name of the driver listed?

Also, go into Applications/Accessories/Terminal and type this in:

```
lspci
```

Post the output of that into a code box here (Listed when you hit reply as a "#" sign).

---

### Post by agim on 2008-02-17
post the output of these two commands

lspci | grep Network

iwconfig

---

### Post by kittykatmeowmeow on 2008-02-17
lspci=
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


I tried the other command and it didn't do anything

---

### Post by Presto123 on 2008-02-17
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

That is your Wireless card...does it say in Restricted Drivers Manager that this (Atheros) is in use?

*Edit: I just noticed that I tried to help you with this when you were using the live CD. Sorry it hasn't worked yet.*

---

### Post by agim on 2008-02-17
really? iwconfig did nothing? Thats real strange.
oh well.
What was the name of the driver listed in the restricted driver manager?
If it continues to give you problems, you may have to download the driver from here
[http://members.driverguide.com/driver/detail.php?driverid=919393](http://members.driverguide.com/driver/detail.php?driverid=919393)
and use ndiswrapper. I hear about problems with ndiswrapper a little more often than makes me comfortable, but I have used it on several installs with several computers and haven't had a problem.

---

### Post by spiderbatdad on 2008-02-17
ndiswrapper-common, ndiswrapper-utils, and ndisgtk are all in synaptic. I would recommend ndisgtk as a graphical frontend to help you set up ndiswrapper.

---

### Post by Presto123 on 2008-02-17
*Edit: You can try this...but spiderbatdat's idea may be easier for you.*

Ndiswrapper has a link to the driver. I would actually suggest using their link as it has been tested. (It may not make any difference, but try it anyway.)

Link to Ndiswrapper:
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Link to driver info and download link (Ctrl+F and paste in "AR5006EG") :
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_a/)

---

### Post by Presto123 on 2008-02-17
> **spiderbatdad said:**
> ndiswrapper-common, ndiswrapper-utils, and ndisgtk are all in synaptic. I would recommend ndisgtk as a graphical frontend to help you set up ndiswrapper.

Sounds like a great idea. +1

Synaptic is System/Administration/Synaptic Package Manager

---

### Post by zwilliams83 on 2008-02-17
Try reading through this post and see if it helps you get things working. I had to completely remove the wifi manager that came preinstalled on Ubuntu and replace it with Wifi-Radar to get it to work on a Compaq F500,

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Good luck!

---

### Post by kittykatmeowmeow on 2008-02-17
I am not running off the live cd anymore.  I added a windows partition.
here is what the iwconfig came up with:
lo        no wireless extensions.

eth0      no wireless extensions

The driver in the Restricted Drivers section is:
Atheros Hardware Access Layer (HAL)

---

### Post by Presto123 on 2008-02-17
> **kittykatmeowmeow said:**
> I am not running off the live cd anymore.  I added a windows partition.
here is what the iwconfig came up with:
lo        no wireless extensions.

eth0      no wireless extensions

The driver in the Restricted Drivers section is:
Atheros Hardware Access Layer (HAL)

LOL...I know you're not. I was just realizing that I tried to help you before.

---

### Post by kittykatmeowmeow on 2008-02-17
LOL!!  Thats cool!  I just really need this WIFI thing to work.... I appreciate all the help.:KS

---

### Post by kittykatmeowmeow on 2008-02-17
I am so confused now...what is this NDISwrapper??

---

### Post by kittykatmeowmeow on 2008-02-17
I found the driver for the card on that site, but when I extracted it and clicked on setup it couldn't find an application to open it with.  now what?

---

### Post by Presto123 on 2008-02-17
> **spiderbatdad said:**
> ndiswrapper-common, ndiswrapper-utils, and ndisgtk are all in synaptic. I would recommend ndisgtk as a graphical frontend to help you set up ndiswrapper.

Kitty, I would try to follow what he has posted here. Do you understand where everything is located with this tip?

---

