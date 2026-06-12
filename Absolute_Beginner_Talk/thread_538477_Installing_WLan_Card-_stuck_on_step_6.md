---
title: "Installing WLan Card- stuck on step 6"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Rays523 on 2007-08-30
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

I did some searching and this guide was very well written but at number six i get this as a result

ray@InsanePyrDragon:~$ sudo depmod -a
ray@InsanePyrDragon:~$ sudo modprobe ndiswrapper
ray@InsanePyrDragon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


and thats it.

What do I do now?

---

### Post by splintercellguy on 2007-08-30
What's the output of ndiswrapper -l?

---

### Post by Rays523 on 2007-08-30
ray@InsanePyrDragon:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present
ray@InsanePyrDragon:~$

---

### Post by kevdog on 2007-08-30
Please post lshw -C network

---

### Post by Rays523 on 2007-08-30
ray@InsanePyrDragon:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@03:08.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:d6030000-d603ffff iomemory:d6020000-d602ffff irq:5
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@03:0c.0
       logical name: eth0
       version: 02
       serial: 00:17:31:d6:66:b0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A ip=71.68.29.32 latency=32 mingnt=255 multicast=yes
       resources: iomemory:d6000000-d601ffff ioport:a800-a83f irq:19
ray@InsanePyrDragon:~$

---

### Post by kevdog on 2007-08-30
Here are my ndiswrapper instructions.  Im not sure where you are.  Just skim them until you get to where you are now.

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

---

### Post by Rays523 on 2007-08-30
ray@InsanePyrDragon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:D6:66:B0  
          inet addr:71.68.29.32  Bcast:255.255.255.255  Mask:255.255.224.0
          inet6 addr: fe80::217:31ff:fed6:66b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:532863 (520.3 KiB)  TX bytes:119282 (116.4 KiB)
          Base address:0xa800 Memory:d6000000-d6020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

ray@InsanePyrDragon:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 8
       bus info: pci@03:08.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:d6030000-d603ffff iomemory:d6020000-d602ffff irq:5
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@03:0c.0
       logical name: eth0
       version: 02
       serial: 00:17:31:d6:66:b0
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=N/A ip=71.68.29.32 latency=32 mingnt=255 multicast=yes
       resources: iomemory:d6000000-d601ffff ioport:a800-a83f irq:19
ray@InsanePyrDragon:~$ gksu gedit /etc/iftab
(gedit:6182): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.




I dont seem to be able to get my computer to "see" a Wlan device :confused::confused:

---

### Post by kevdog on 2007-08-30
Its because you dont have a driver installed.

Did you 
sudo depmod -a
sudo modprobe ndiswrapper
echo ndiswrapper | sudo tee -a /etc/modules

and finally reboot??

---

### Post by Rays523 on 2007-08-30
Yep, but I think that I might of downloaded a 32bit driver :(

and I have a 64bit version of ubuntu, so therefore the driver didn't install :KS

Golden star for ME.

I'll try and get a 64bit driver later on tonight.

---

### Post by Rays523 on 2007-09-13
Okay Im still without wireless, I found a Marvell driver but when I try to use ndiswrapper on the .inf file it give me something like

error file not found at usr/sbin/ndiswrapper line 217

and then when I do ndiswrapper -l  
 
it list the driver and says driver invalid.

Anybody know how to get it working with 64 bit Im kinda stuck I really want to permanently ditch windows.

---

### Post by Rays523 on 2007-09-14
somebody plz tell me i am missing something incredably ez and stupid, that way i can fix it

:(

---

### Post by splintercellguy on 2007-09-14
Did you copy all the driver files, or just the INF? You need all of them.

---

### Post by crjackson on 2007-09-18
Ray,

Did you have the *.sys file in the same folder at the *.inf file when you loaded this?

---

### Post by crjackson on 2007-09-18
Ray, it looks like to me that a driver is actually installed, but if I were you, I would beg for help from kevdog.  It took me two weeks and about 90 posts to get mine worked out.  **_If anyone can help you it's kevdog. _** Don't give up.

[B]> **Rays523 said:**
> ray@InsanePyrDragon:~$ ndiswrapper -l
mrv8000c : driver installed
        device (11AB:1FAA) present
ray@InsanePyrDragon:~$[/B]

---

### Post by Rays523 on 2007-09-18
i copied the inf and sys files, the wireless card had never been recognized but the ethernet works.

---

### Post by crjackson on 2007-09-19
> **Rays523 said:**
> i copied the inf and sys files, the wireless card had never been recognized but the ethernet works.

Hang in there buddy, I've requested the expert have a look when he gets time...

---

### Post by kevdog on 2007-09-19
There is no expert around here (noob12??).  Anyway its probably b/c you didnt uninstall or remove the old driver.

Do the following:
sudo rm -R /etc/ndiswrapper/*

Now try reinstalling the driver:

the sudo ndiswrapper *******.inf   line.

---

### Post by Rays523 on 2007-09-19
Okay I'll give that a shot.

when will the sudo -i ~/ubuntu/home/makeeverythingworkrightnow

command come out? because that would be really nice.

:lolflag:

BTW I hate windows more and more with each passing hour I spend on my computer :-x

---

### Post by crjackson on 2007-09-19
> **Rays523 said:**
> Okay I'll give that a shot.

when will the sudo -i ~/ubuntu/home/makeeverythingworkrightnow

command come out? because that would be really nice.

Next month.  Please hold your breath...:)

---

