---
title: "broadcom netlink bcm5789"
date: 2013-12-13
forum: Any Other OS
---

### Post by grouchyolddude on 2013-12-13
looking for compatible driver and installation help... just installed linux lite 1.0.6. I would like to dl to a thumb drive and then install on a Sharp laptop

---

### Post by varunendra on 2013-12-15
The required driver (tg3) for this card is already available in the kernel, you shouldn't need to install it from elsewhere.
Is the card not working?

**PS:**
By the way, Linux Lite is not Ubuntu. :)

---

### Post by QIII on 2013-12-15
*Moved to **Other OS/Distro Support.***

---

### Post by grouchyolddude on 2013-12-15
> **varunendra said:**
> The required driver (tg3) for this card is already available in the kernel, you shouldn't need to install it from elsewhere.
Is the card not working?

**PS:**
By the way, Linux Lite is not Ubuntu. :)

no it isn't working. I guess... I have no wireless network showing. 'n sorry 'bout the lite question in the incorrect area (ubuntu). What experience I have, is primarily been with ubuntu.

---

### Post by varunendra on 2013-12-15
BCM5789 is not a wireless device, it is an Ethernet chip. If you are after wireless, we still need to see what chip you have.

IF, it is wireless we are going to troubleshoot here, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It should give us everything we need to know to start "Mission Wireless", and probably to accomplish it too.

---

### Post by grouchyolddude on 2013-12-15
well maybe I'm not smart enough to pull this off. :( I don't have internet access with the laptop. I went to the 'dropbox' link in your post, ([http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)) but failed to find or see a program to dl. to save, to run. I see a long script, but I'm lost. Sorry for being such a boot.

---

### Post by varunendra on 2013-12-15
Ah, no worries about that. I'm attaching it in a tar.bz2 compressed form.

Just download the attachment > copy or move it to your Desktop > Right-click > Extract Here

Then open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
cd Desktop
./wireless_script
```
Don't forget the leading dot (.) in the second command. Supply your login password when prompted. It should create a file "wireless-info.txt" (or "wireless-info.txt.tar.gz") on the Desktop.

Attach this file or post its contents in your next post. If posting contents here, please wrap it within 'Code' tags (follow the "Using Code Tags" link in my signature to see how).

---

### Post by grouchyolddude on 2013-12-16
```

*************** info trace ***************

***** uname -a *****

Linux ole-PC-AL3D 3.2.0-40-generic-pae #64-Ubuntu SMP Mon Mar 25 21:44:41 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Linux Lite 1.0.6
Release:	12.04
Codename:	precise

***** lspci *****

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express [14e4:169d] (rev 11)
	Subsystem: Sharp corporation Device [13bd:1040]
	Kernel driver in use: tg3

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 8644:800b  

***** PCMCIA Card Info *****


***** iwconfig *****


***** rfkill *****


***** lsmod *****


***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****


***** udev rules *****

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

***** dmesg *****

[   29.341558] intel_rng: don't want to disable this in firmware setup, and if

****************** done ******************

```

THANK YOU~ for making this stupid proof for me :)

---

### Post by varunendra on 2013-12-16
There is no trace of wireless in your system. If there ever was a wireless card in it, either it is physically disconnected, or is completely dead.

If you are sure your system had (or 'has') a wireless card in it, please check your BIOS to make sure it is detected and enabled, and if it already is, try resetting the BIOS to factory defaults. Although I don't think disabling it from BIOS can make it completely disappear as it currently seems.

---

### Post by grouchyolddude on 2013-12-16
Well THANK YOU! I guess that answers that question.

---

### Post by varunendra on 2013-12-17
You're welcome ! :)

USB wireless dongles are dirt-cheap these days if you need wireless. Just be sure to get one that is well known to work smoothly with Linux. You can browse the "[Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336")" section of the forums to do the research. Or you can pick a few models from [this page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), and THEN browse the forums to make sure they don't have any issues that can't be easily fixed.

---

### Post by grouchyolddude on 2013-12-19
Uhg!... Someday I'm going to learn to do my research "FIRST"... I bought a "Comfast" Model:	
CF-WU720N. $5 deliverd off evilbay :p
  BUT.......  I pulled a few  screws off the back and looked inside, and the machine certainly does have a wireless card in it. I tried the latest kubuntu 13.1 ver. but it doesn't see the card either.

---

### Post by varunendra on 2013-12-19
> **grouchyolddude said:**
> Uhg!... Someday I'm going to learn to do my research "FIRST"... I bought a "Comfast" Model:	
CF-WU720N. $5 deliverd off evilbay :p
  BUT.......  I pulled a few  screws off the back and looked inside, and the machine certainly does have a wireless card in it. I tried the latest kubuntu 13.1 ver. but it doesn't see the card either.

If you have or can have access to a different laptop which has a similar card (same PCI specs) in it, try swapping the cards (the other card in this lappy and this card in the other one) and see if you have something significant to report.

---

