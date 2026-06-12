---
title: "MBP 5,2 -- Screen brightness"
date: 2009-03-02
forum: Apple Hardware Users
---

### Post by darkcarnival on 2009-03-02
Is it impossible to control screen brightness on a MBP 5,2 ?

I've tried the suggestions available at:
[https://help.ubuntu.com/community/MacBookPro5-1/Intrepid](https://help.ubuntu.com/community/MacBookPro5-1/Intrepid)

Which suggests enabling the Mac PPA repo, downloading and loading the module "mbp_nvidia_bl" which gives me:
```

FATAL: Error inserting mbp_nvidia_bl (/lib/modules/2.6.27-11-generic/updates/dkms/mbp_nvidia_bl.ko): No such de

```

And I've tried both suggestions here:
[https://help.ubuntu.com/community/MacBook%20Aluminum#Screen%20brightness%20adjustment](https://help.ubuntu.com/community/MacBook%20Aluminum#Screen%20brightness%20adjustment)

One of which (again) tells me that mbp_nvidia_bl can't load (same error as before) and the other, nvclock tells me this after I try adjusting brightness with my compiled version:

```

nvclock -S 10
Unhandled init script entry with id '&#65533;' at ea4d
Unhandled init script entry with id '&#65533;' at ea97
Unhandled init script entry with id '&#65533;' at eaba
Unhandled init script entry with id '&#65533;' at eadd
Unhandled init script entry with id '&#65533;' at ea4d
Unhandled init script entry with id '&#65533;' at ea97
Unhandled init script entry with id '&#65533;' at eaba
Unhandled init script entry with id '&#65533;' at eadd
Error!
Smartdimmer is only supported on certain (HP/Samsung/Sony/Zepto) laptops using a Geforce 6200/7x00Go/8x00Go. If you want support on your laptop contact the author.

```

Other information:
**lspci**
```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 07)

```

**lscpi -n **
```

00:00.0 0600: 10de:0a82 (rev b1)
00:00.1 0500: 10de:0a88 (rev b1)
00:03.0 0601: 10de:0aae (rev b3)
00:03.1 0500: 10de:0aa4 (rev b1)
00:03.2 0c05: 10de:0aa2 (rev b1)
00:03.3 0500: 10de:0a89 (rev b1)
00:03.4 0500: 10de:0a98 (rev b1)
00:03.5 0b40: 10de:0aa3 (rev b1)
00:04.0 0c03: 10de:0aa5 (rev b1)
00:04.1 0c03: 10de:0aa6 (rev b1)
00:06.0 0c03: 10de:0aa7 (rev b1)
00:06.1 0c03: 10de:0aa9 (rev b1)
00:08.0 0403: 10de:0ac0 (rev b1)
00:09.0 0604: 10de:0aab (rev b1)
00:0a.0 0200: 10de:0ab0 (rev b1)
00:0b.0 0101: 10de:0ab5 (rev b1)
00:0c.0 0604: 10de:0ac4 (rev b1)
00:15.0 0604: 10de:0ac6 (rev b1)
00:16.0 0604: 10de:0ac7 (rev b1)
00:17.0 0604: 10de:0ac7 (rev b1)
02:00.0 0300: 10de:0647 (rev a1)
04:00.0 0280: 14e4:432b (rev 01)
05:00.0 0c00: 11c1:5901 (rev 07)

```

**nvclock -info -f**
```

Unhandled init script entry with id '&#65533;' at ea4d
Unhandled init script entry with id '&#65533;' at ea97
Unhandled init script entry with id '&#65533;' at eaba
Unhandled init script entry with id '&#65533;' at eadd
Unhandled init script entry with id '&#65533;' at ea4d
Unhandled init script entry with id '&#65533;' at ea97
Unhandled init script entry with id '&#65533;' at eaba
Unhandled init script entry with id '&#65533;' at eadd
-- General info --
Card: 		nVidia Geforce 9600M GT
Architecture: 	G96 C1
PCI id: 	0x647
GPU clock: 	182.248 MHz
Bustype: 	PCI-Express

-- Shader info --
Clock: 648.000 MHz
Stream units: 32 (11b)
ROP units: 8 (b)
-- Memory info --
Amount: 	512 MB
Type: 		128 bit DDR3
Clock: 		594.000 MHz

-- PCI-Express info --
Current Rate: 	1X
Maximum rate: 	16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 53C

-- VideoBios information --
Version: 62.94.78.00.08
Signon message: G96 E565 NB9P-APPLE VGA BIOS
Performance level 0: gpu 279MHz/shader 558MHz/memory 297MHz/0.90V/100%
Performance level 1: gpu 393MHz/shader 786MHz/memory 700MHz/0.93V/100%
Performance level 2: gpu 500MHz/shader 1250MHz/memory 792MHz/1.00V/100%
VID mask: f
Voltage level 0: 0.90V, VID: f
Voltage level 1: 0.93V, VID: e
Voltage level 2: 1.00V, VID: b


```

---

### Post by cyberdork33 on 2009-03-02
try just nvidia_bl

---

### Post by inphektion on 2009-03-02
I'm on MBP 5,2 and using Jaunty.  Are you on Jaunty or Intrepid?
Either way it seems you'd want mbp-nvidia-bl-dkms.  That installs for me.  
Can you install usbhid-dkms?

---

### Post by cyberdork33 on 2009-03-02
> **inphektion said:**
> I'm on MBP 5,2 and using Jaunty.  Are you on Jaunty or Intrepid?
Either way it seems you'd want mbp-nvidia-bl-dkms.  That installs for me.  
Can you install usbhid-dkms?
I haven't installed either as I do not have a 5th gen MacBook or Macbook pro.

You may be right though, I just noticed some changes on a wiki page today, that lead me to think maybe the other is fine in jaunty. If it doesn't work, then you can always go back.

---

### Post by darkcarnival on 2009-03-02
As I understand it, nvidia_bl is a module that is based upon the way that nvclock handles things.

Nevertheless I've tried it anyway.. I can modprobe it, it loads. I can then try to write a value to the file (as root)
```

# echo 100 | tee -a /sys/class/backlight/nvidia_backlight/brightness
100

```

Nothing further is happening, if I read the file it does display '100' but no changes was made to my backlight. The same happens for any other value between 0-250'ish.


If it works for you. Would you mind checking the version of your macbook like so:
```

dmidecode -s system-product-name

```

Mine's ```
MacBookPro5,2
```

---

### Post by inphektion on 2009-03-02
Well I have nothing at all in /sys/class/backlight.  the dmidecode does show macbookpro 5,2. Here is facter output which shows all specs so you see exactly what I'm on:
```

root@nihility:~# facter
architecture => x86_64
domain =>
facterversion => 1.5.1
fqdn => nihility
hardwaremodel => x86_64
hostname => nihility
interfaces => eth0,eth1,pan0
ipaddress => 10.1.16.49
ipaddress_eth0 => 10.1.16.49
ipaddress_eth1 => 10.1.16.55
kernel => Linux
kernelrelease => 2.6.28-8-generic
kernelversion => 2.6.28
lsbdistcodename => jaunty
lsbdistdescription => Ubuntu jaunty (development branch)
lsbdistid => Ubuntu
lsbdistrelease => 9.04
macaddress => 00:23:df:9b:68:42
macaddress_eth0 => 00:23:df:9b:68:42
macaddress_eth1 => 00:23:6c:98:fe:bf
macaddress_pan0 => 8e:b7:32:00:d7:78
manufacturer => Apple Inc.
memoryfree => 7.19 GB
memorysize => 7.68 GB
netmask => 255.255.252.0
netmask_eth0 => 255.255.252.0
netmask_eth1 => 255.255.252.0
operatingsystem => Ubuntu
operatingsystemrelease => 2.6.28-8-generic
processor0 => Intel(R) Core(TM)2 Duo CPU     T9800  @ 2.93GHz
processor1 => Intel(R) Core(TM)2 Duo CPU     T9800  @ 2.93GHz
processorcount => 2
productname => MacBookPro5,2
ps => ps -ef
rubysitedir => /usr/local/lib/site_ruby/1.8
rubyversion => 1.8.7
serialnumber => 
swapfree => 4.00 GB
swapsize => 4.00 GB
type => Portable
virtual => physical

```

the nvidia-bl-dkms did install successfully but i didn't try changing brightness, I was going to get the keyboard Fn buttons working next to try that as I don't know how else to modify brightness, it seems to always be at 100 right now.
Even though i'm on jaunty i've added the mactel PPA repos from intrepid.

---

### Post by inphektion on 2009-03-02
ah but yes if i modprobe mbp_nvidia_bl I get the same can't load error.  If I modprobe nvidia_bl I get module not found.

---

### Post by darkcarnival on 2009-03-03
I don't think you've understood. I have the same kind of macbook as you do (without the hefty CPU/RAM upgrades, sadly :P ) -- and I made this thread exactly because I *couldn't* get the brightness adjustment working on a MacbookPro5,2.

If you *insist* on trying to no avail. Then I can tell you that the nvidia_bl module is from the nvidia-bl-dkms package available in the Mactel PPA repository :)

(Side question: Could you really even load mbp_nvidia_bl ? )

---

### Post by _mario_ on 2009-03-03
> **darkcarnival said:**
> Is it impossible to control screen brightness on a MBP 5,2 ?

I've tried the suggestions available at:
[https://help.ubuntu.com/community/MacBookPro5-1/Intrepid](https://help.ubuntu.com/community/MacBookPro5-1/Intrepid)

Which suggests enabling the Mac PPA repo, downloading and loading the module "mbp_nvidia_bl" which gives me:
```

FATAL: Error inserting mbp_nvidia_bl (/lib/modules/2.6.27-11-generic/updates/dkms/mbp_nvidia_bl.ko): No such de

```


yes. you're right. the driver didn't support the MacBookPro 5,2 until now. i've uploaded a new version a few minutes ago.

ps: nvidia_bl as well as nvclock did never work on the MacBookPro 5,1 and are most likely to not work on your machine as well. the reason is still unknown...

since we are talking about MacBookPro 5,2: is there also a new MacBook 5,2 available?

ciao,
Mario

---

### Post by darkcarnival on 2009-03-03
That sounds nothing short of awesome ! :)

Mind telling where you've posted it though ? The Mactel PPA isn't reporting any updates.

---

### Post by cyberdork33 on 2009-03-03
> **darkcarnival said:**
> Mind telling where you've posted it though ? The Mactel PPA isn't reporting any updates.It takes awhile to build and post. Please be patient.

---

### Post by _mario_ on 2009-03-03
> **darkcarnival said:**
> That sounds nothing short of awesome ! :)

Mind telling where you've posted it though ? The Mactel PPA isn't reporting any updates.

strange. the package has been available some minutes after upload.

```

mario@snoopy:~> apt-cache policy mbp-nvidia-bl-dkms
mbp-nvidia-bl-dkms:
  Installed: 0.19~jaunty
  Candidate: 0.19~jaunty
  Version table:
 *** 0.19~jaunty 0
        500 http://ppa.launchpad.net jaunty/main Packages
        100 /var/lib/dpkg/status
     0.19~intrepid 0
        500 http://ppa.launchpad.net intrepid/main Packages

```

did you update, upgrade, and reboot?

ciao,
Mario

---

### Post by cyberdork33 on 2009-03-03
and change your sources.list to point to jaunty instead of intrepid ;)

---

### Post by inphektion on 2009-03-03
works great!

different usage now.
looks like brightness is from 0-15 and I was successfully changing it with 
echo 15 > /sys/class/backlight/mbp_backlight/brightness for max brightness.

Is there a wiki for MBP5,2 or would it be the same for 5,1?

I'd like to get a Jaunty MBP5,2 wiki going as we move through things.

---

### Post by darkcarnival on 2009-03-03
cyberdork33: I was asking where he put the sources so that I could've done the compiling and package creating myself ;)

---

### Post by cyberdork33 on 2009-03-03
> **inphektion said:**
> Is there a wiki for MBP5,2 or would it be the same for 5,1? I think it should be the same. Usually the ,2 models are the same as the predecessor except the cpu speed has been bumped up or something.

> **inphektion said:**
> I'd like to get a Jaunty MBP5,2 wiki going as we move through things.Go for it. Have a look at how the MacbookPro2,1 / 2,2 share a page, and try to match that naming scheme if you would.

There is information at the MactelSupportTeam wiki page with guidelines and templates for docs.
[https://wiki.ubuntu.com/MactelSupportTeam/](https://wiki.ubuntu.com/MactelSupportTeam/)

> **darkcarnival said:**
> cyberdork33: I was asking where he put the sources so that I could've done the compiling and package creating myself ;)well, you upload them to the PPA... It is a server that you upload the source to and it compiles it and posts it so that it is available to users. Once it is posted, you can go to the mactel-support ppa page in launchpad and download the source package manually if you want:
[https://edge.launchpad.net/~mactel-support/+archive/ppa](https://edge.launchpad.net/~mactel-support/+archive/ppa)

---

