---
title: "Wireless card help pl"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Kedster on 2007-09-05
Integrated 10/100 Network Card • Integrated Wireless LANi have that wireless card with the rest of the specs in my sig( is there a better way to present it so every one can get it easy) and need help to set it up plese 
i have a 3 foot cord to go to my comp from my roauter wich is very resraning please help

---

### Post by ConradPafford on 2007-09-05
The best solution I can think of (since you didn't put the type of wireless card) is to first determine the manufacturer of the wireless card.
1. What is the model of the laptop that you are using?
2. Visit  the laptops manufactures page.
3. Enter the serial number or manufacturer number of the laptop to find out the Wireless card used.
4. If the above fails take the darn thing apart and find the information necessary by looking at the card.
5. After determining the make of the wireless card look for a linux driver by googling.

The above steps might sound a bit babyish but I hope they help ... that is my intention


Conrad

---

### Post by anewguy on 2007-09-05
If you can post the output of    lspci   back here, we might be able to help you.:)

---

### Post by Kedster on 2007-09-05
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
kedster@spadhawk:~$

---

### Post by crjackson on 2007-09-05
**02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**

This is your wireless card.  I have the same one and it works great.

Go to the thread listed below and READ it all before you start.  It got me up and running in about 20 minutes.

Me posting the instructions again would just be duplicating work that's been done many times already.  Besides the people in that thread know more about what they are doing.

[http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902")

---

### Post by ConradPafford on 2007-09-06
Off TOPIC
That looks like a mad mongoose in your avatar -- haha cute little ferocious thing!

---

### Post by Kedster on 2007-09-06
ummm the guide didnt work is there a nother way to dod it like with more GUI 
cuz errors come up and i tried to copy them but t just wouldent work

---

### Post by Kedster on 2007-09-06
please

---

### Post by Kedster on 2007-09-07
when i try to install ndiswrappper  this messege comes up 
Please insert the disk labeled:
Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)
in drive /cdrom/

---

### Post by Kedster on 2007-09-07
please help me

---

### Post by Kedster on 2007-09-08
umm like i did start this i need help i need wirless

---

### Post by Kedster on 2007-09-08
this is the thing it says whent wrrong when i try to install ndiswrapper

W: Failed to fetch cdrom:[Edubuntu 7.04 _Feisty Fawn_ - Release i386 Binary-1 (20070415)]/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb

PS wat does ndiswrapper mean

---

### Post by Kedster on 2007-09-08
like r u guys egnoreing me

---

### Post by Kedster on 2007-09-08
like please

---

### Post by Kedster on 2007-09-08
is it that u cant help me or u dont want to

---

### Post by Kedster on 2007-09-08
kedster@spadhawk:~$ lspci | grep Broadcom\ Corporation
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
kedster@spadhawk:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules

---

### Post by Kedster on 2007-09-08
bump

---

### Post by xc3RnbFO8P on 2007-09-08
Have you tried this?

[http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom")

---

### Post by Kedster on 2007-09-09
no i diddnt work this came up 
E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1 
while trying to install it

---

### Post by kevdog on 2007-09-09
Here are my ndiswrapper instructions.  Please see very bottom of the thread first to uninstall any old installation before beginning in your case.

To complete **without a working internet** connection you will need:
1. The ubuntu installation cd
2. USB flash drive
3. Another computer with an internet connection to transfer just a few files
4. WinXP drivers for your wireless card (unless you have a RTL chipset in which case you will need the Win98 drivers)
	****Note that if you are doing an installation on Ubuntu 64 bit, that you will need the appropriate WinXP 64 bit driver for your wireless card


This guide is now getting rather long.  It is organized into the following sections
1. Installation of ndiswrapper and windows drivers from source files (what most people want)
2. Ensuring that your wireless interface is on wlan0 and not some other interace (eth1,ath1,etc)
3. Modification of /etc/network/interfaces file (for those wanting to use NetworkManager)
4. Common Tips Problems, Suggestions (This section is continually growing, check here first if you have a problem)

**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)

We are grabbing ndiswrapper-1.48-rc1

***The following section will work if you have an internet connection
*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz)
Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory.  Continue with the next following set of instructions
```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 
cd ndiswrapper

```

Extract, compile, and install ndiswrapper
```
tar -zxvf ndiswrapper-1.48rc1.tar.gz
cd ndiswrapper-1.48rc1
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Window's wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files (see below).
In addition, please turn off any (WEP/WPA/MAC filtering) that may be present in the router.  This is to confirm that the basic ndiswrapper setup can connect to an unencrypted network.  Instructions how to configure for WEP/WPA encryption are included in another separate guide. 

Ndiswrapper by default assumes your card to be assigned to the interface wlan0 -- this may or may not be the case.
If after rebooting, and you issue the following command:
```
ifconfig
```
And you do not see an interface named wlan0, then continue.
Below are some strategies that I have used to ensure that your wireless device is assigned to the wlan0 interface.

**Verification/Modification of /etc/iftab file**

The /etc/iftab file acts to permanently asssociate a given MAC Address with an interface name.  Additions in this file are only necessary if you need to lock down the interface name with a MAC Address.  First discover what interface name is currently associated to your network card MAC Address:
```
lshw -C network
```

Example output:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       **serial: 00:12:17:35:17:10 **
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

In the example above my card's MAC Address - 00:12:17:35:17:10 - is currently assigned to wlan0 (logical name line).  If your card is assigned to a different logical name (such as eth1, ath0, ra0), then modifications will be needed to your /etc/iftab file.  

To modify your /etc/iftab file:
```
gksu gedit /etc/iftab
```

You will need to ensure your interface name is associated with wlan0 rather than a different interface name. There are two ways to accomplish this: 
#1) Let the computer do it automatically at boot, 
#2) Manually make the association  

In case #1 manually comment all the associations listed in your /etc/iftab file -- allow the computer to assign them internally at boot.  **This solution is probably the most viable for most users.**  An example of how to accomplish this:  

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1

```

Because the association of eth1 with the MAC Address was commented, the computer will internally and automatically make the assocation of an interface name with the MAC address.  This process of associating wlan0 with the networking device's MAC Address should work about 99% of the time.  If for some reasom it does not, proceed to step #2.

In case #2 - Manually make the association you need to ensure there is only one MAC address associated with one interface name.

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

#eth1 mac 00:12:17:35:17:10 arp 1
wlan0 mac 00:12:17:35:17:10 arp 1

```

In this example the old interface associated of eth1 was commented, and the new association of wlan0 to the card MAC address was made manually.

If modification of the /etc/iftab file was performed, a reboot is recommended at this time.
```
sudo shutdown -r now
```

**Modification of /etc/network/interfaces file**

First step is to comment out all the unnecessary interface names with the file.  In order to discover what interface names are currently needed:

```
lshw -C network
```
With all the devices listed, note their logical names.  An example:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       **logical name: wlan0**
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1 ip=192.168.1.101 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11

```

Only the names mentioned with this command need to be listed in the /etc/network/interfaces file (along with the loopback address).

First backup your current interface file configuration in case something goes wrong:
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

To modify your /etc/network/interfaces file:
[CODE]gksu gedit /etc/network/interfaces
```


A basic interface file, might include the following (assuming a wired ethernet device is present - eth0, and the wireless device installed with ndiswrapper - wlan0) -- Note in this example I commented out the old eth1 interface -- I could have also removed these lines to have the same effect.

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

```

Further modications may be needed to this file, depending if you need to run your card in roaming mode (convenient with laptops that often connect to different routers of networks), configure your card with static IP address, desire to set WEP/WPA authentication parameters manually, etc.  Again there are many possibilites at this point, far too many to list the different permutations, however this gives you a basic starting point.


**[SIZE="4"]Common Tips Problems, Suggestions[/SIZE]**

Suggestions:
1. The command **[SIZE="3"]lshw -C network[/SIZE]** always tells you what driver you are using. Here is an example:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="3"]driver=ndiswrapper+lsbcmnds driverversion=1.48rc1+Cisco-Linksys ,LLC.,02/1[/SIZE]** ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11


```

If you are having a problem after the installation, ensure that you have the correct version of ndiswrapper installed, and that you are not using another driver.

2. Discovering your chipset -- You can always find the chipset of your pci wireless device with the following command (***Note this will not work for wireless USB dongles):

```
lspci -nn | grep Network
```

3. **Broadcom chipset users** -- Be sure to blacklist the bcm43xx driver in the /etc/modprobe.d/blacklist file

For broadcom chipset users, in most cases you will need to blacklist the native bcm43xx drivers since they take precedence over ndiswrapper.  If after installing ndiswrapper, and things are not working, and you check lshw -C network and you find the following:
```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 03
       serial: 00:12:17:35:17:10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="3"]bcm43xx[/SIZE]** ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:3c000000-3c001fff irq:11


```

You need to do ONE of the following to solve this problem:
a. At command line type:
```
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
```

b. Manually edit the /etc/modprobe.d/blacklist file: (```
gksu gedit /etc/modprobe.d/blacklist
```), and add the following:
```
blacklist bcm43xx
```

4. INVALID DRIVER - Ive installed ndiswrapper but when I try to install the Windows driver Im getting a line that states:

```

root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
root@dhcppc1 ndiswrapper-1.47]# /usr/sbin/ndiswrapper -l
bcmwl5 : invalid driver!
driver : invalid driver!

```

This error usually means that there are duplicate or more than one driver installed with ndiswrapper.  The easiest way to resolve this message is to do the following:

```
sudo rm -R /etc/ndiswrapper *
```

You will then have to reinstall your windows driver via.
```
sudo ndiswrapper **********.inf  <-----Substitue the appropriate name of your inf file here.
```

5. I tried install ndiswrapper from repository before I found this guide.  How do I uninstall it??

**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**

These are instructions for manual un-installation of ndiswrapper.  I would suggest if you installed ndiswrapper from repository with use of Synaptic, apt-get(aptitude), or some other means (Aptitude), you use the same means to uninstall the ndiswrapper program.  Sometimes however un-installation via these means are unsuccessful and the following steps are necessary.  These steps are also necessary if you have ever installed ndiswrapper from source sometime in the past.

Dont worry if some of these commands don't do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

---

