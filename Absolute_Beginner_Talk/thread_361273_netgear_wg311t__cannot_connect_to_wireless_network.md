---
title: "netgear wg311t : cannot connect to wireless networks"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by kdellaquila on 2007-02-14
i just installed ubuntu on my computer.  while it is able to detect wireless internet connections whenever i try and connect, it fails.

it is a netgear 108mbps wireless pci adapter wg311t.

thanks in advance.

---

### Post by ukripper on 2007-02-14
> **kdellaquila said:**
> i just installed ubuntu on my computer.  while it is able to detect wireless internet connections whenever i try and connect, it fails.

it is a netgear 108mbps wireless pci adapter wg311t.

thanks in advance.

in terminal window run following comands and paste the output here:

$ sudo lspci

$ sudo lsusb

$ sudo iwconfig

---

### Post by kdellaquila on 2007-02-15
here goes:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

kdellaquila@kdellaquila:~$ **sudo lspci**
Password:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
03:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
kdellaquila@kdellaquila:~$ **sudo lsusb**
Bus 002 Device 002: ID 04b3:3025 IBM Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 047d:105e Kensington 
Bus 001 Device 006: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. 
Bus 001 Device 005: ID 04b3:310c IBM Corp. 
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000  
kdellaquila@kdellaquila:~$ **sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"teh internets"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3731-3834-3635-3439-3338   Security mode:restricted
          Power Management:off
          Link Quality=19/94  Signal level=-76 dBm  Noise level=-95 dBm
          Rx invalid nwid:10599  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kdellaquila@kdellaquila:~$

---

### Post by ukripper on 2007-02-16
> **kdellaquila said:**
> here goes:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

kdellaquila@kdellaquila:~$ **sudo lspci**
Password:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
03:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
kdellaquila@kdellaquila:~$ **sudo lsusb**
Bus 002 Device 002: ID 04b3:3025 IBM Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 047d:105e Kensington 
Bus 001 Device 006: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. 
Bus 001 Device 005: ID 04b3:310c IBM Corp. 
Bus 001 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000  
kdellaquila@kdellaquila:~$ **sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"teh internets"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3731-3834-3635-3439-3338   Security mode:restricted
          Power Management:off
          Link Quality=19/94  Signal level=-76 dBm  Noise level=-95 dBm
          Rx invalid nwid:10599  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kdellaquila@kdellaquila:~$


Your wireless settings seems to be fine,  try running follwoing

$ sudo ifdown ath0

$ sudo ifup ath0

Then install wlassistant :

$ sudo apt-get install wlassistant 

To run wlassistant you need to use Terminal if you are using gnome not KDE:

So type:

$ sudo wlassistant

configure your access point with ESSID, WEP KEY and auto DHCP and don't forget to tick on ASCII check box.

---

### Post by kdellaquila on 2007-02-16
thanks!  do i need to be connected to the internet to install wlassistant ?

---

### Post by ukripper on 2007-02-16
> **kdellaquila said:**
> thanks!  do i need to be connected to the internet to install wlassistant ?

Yes, you will need internet to get wlassistant package. so probably you can just plug ethernet cable to eth0.

---

### Post by Janeric on 2007-02-16
Hi I am a newbie on Ubuntu.
Would this thread also be useful for 3com 3CRDAG675B pci-card. The card is found but I have WEP-key on router and could only find KWLAN to do these things, but that is under KDE and Kubuntu. I am not yet ready to change too much.

---

### Post by ukripper on 2007-02-16
> **Janeric said:**
> Hi I am a newbie on Ubuntu.
Would this thread also be useful for 3com 3CRDAG675B pci-card. The card is found but I have WEP-key on router and could only find KWLAN to do these things, but that is under KDE and Kubuntu. I am not yet ready to change too much.

If you are using gnome then you can use KDE packages in terminal window by using **sudo** in front of the package name.

I prefer wlassistant personally as it is easier to configure

---

### Post by kdellaquila on 2007-02-18
still no luck.  the networks show up on wlassistant but i still cannot connect.  i tried entering 
$ sudo ifdown ath0

$ sudo ifup ath0

and i got this:

kdellaquila@kdellaquila:~$ sudo ifdown ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 4726
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:8c:93:b3
Sending on   LPF/ath0/00:14:6c:8c:93:b3
Sending on   Socket/fallback
kdellaquila@kdellaquila:~$ sudo ifup ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:8c:93:b3
Sending on   LPF/ath0/00:14:6c:8c:93:b3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
kdellaquila@kdellaquila:~$

---

### Post by ukripper on 2007-02-19
> **kdellaquila said:**
> still no luck.  the networks show up on wlassistant but i still cannot connect.  i tried entering 
$ sudo ifdown ath0

$ sudo ifup ath0

and i got this:

kdellaquila@kdellaquila:~$ sudo ifdown ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 4726
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:8c:93:b3
Sending on   LPF/ath0/00:14:6c:8c:93:b3
Sending on   Socket/fallback
kdellaquila@kdellaquila:~$ sudo ifup ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 5798864
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:14:6c:8c:93:b3
Sending on   LPF/ath0/00:14:6c:8c:93:b3
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
kdellaquila@kdellaquila:~$

If your available network shows up in wlassistant that means your network card has detected your access point or router. In wlassistant you need to configure your ESSID, WEP KEY and select DHCP to auto and don't forget to tick on check box **ASCII**.

---

### Post by kdellaquila on 2007-02-21
still no luck unfortunately.  i cannot even connect to an unsecured network. wlassistant detects them but i keep getting connection failed.

---

### Post by ZeroThree on 2007-02-22
I'm having the exact same problem. I'm curious if ndiswrapper would fix the problem.. haven't had the chance to try it yet.. just a suggestion.

---

### Post by ubuntu_demon on 2007-02-22
For people who have different wireless cards I would advise you to start a new thread. This will make it easier for people to help you.

Good luck all!

kdellaquila : 
I have editted the thread title to make it reflect that this is about the netgear wg311T.

---

### Post by ubuntu_demon on 2007-02-22
I would suggest to not use ndiswrapper. If you have tried ndiswrapper first undo the steps you have done trying to make it work with ndiswrapper. Then install the restricted modules for your kernel.

$uname -r

Then choose which one to install based on that result :
$ sudo aptitude install linux-generic
$ sudo aptitude install linux-386
$ sudo aptitude install linux-686

This packes makes sure that you will always have the relevant restricted modules even after a kernel upgrade.

Login to your router and set your router to unsecured.

Now do a reboot and configure your network using system->administration->networking.

If all is well now you will have wireless internet :).

Otherwise you might need to modprobe some modules but we'll see about that later if necessary :)

Assuming you have wireless internet :

Now you will need to configure some security settings. One which is very easy is mac-filtering. You can do this in your router and you don't have to do anything on your pc (wireless) settings.

You can additionally use WEP if you decide to use WEP you need to configure this on your router and in system->administration->networking.

Instead of WEP you can use WPA(2). Which is harder to setup. If you decide to do this then here's a guide :
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

I'm very interested in your experiences. I hope you get WPA2 personal running with CCMP/AES. I'm searching for a wireless card myself see :
[http://www.ubuntuforums.org/showthread.php?t=363633](http://www.ubuntuforums.org/showthread.php?t=363633)

the netgear WG311T is one of the candidates

---

### Post by ZeroThree on 2007-02-22
I only have a wifi connection available in my apartment.. I can access the net via windows (running a dual boot XP/Edgy). Is there any way I can download a .deb package version of the restricted modules you mentioned above to an external hd and then install it using dpkg?

---

### Post by ubuntu_demon on 2007-03-01
> **ZeroThree said:**
> I only have a wifi connection available in my apartment.. I can access the net via windows (running a dual boot XP/Edgy). Is there any way I can download a .deb package version of the restricted modules you mentioned above to an external hd and then install it using dpkg?
yeah.
Find out which kernel you are running :
$uname -r

And find the corresponding restricted modules on packages.ubuntu.com (make sure to get them for Edgy if you are running Edgy)

If you need more help post the result of "$uname -r" and let us know.

---

### Post by ZeroThree on 2007-03-03
I haven't had time to play with it.. I ended up hooking up my comp to a wired connection finally, and its midterm season..

I installed all of the packages, and I need to physically put the wifi pci card back in my computer before I can verify that it works. But I'll keep posting...

---

### Post by ubuntu_demon on 2007-03-26
If you have a bit of patience you can wait for Ubuntu Feisty. Feisty's networkmanager is really easy and works with most networks.

I bought a wg311T and I'm using wpasupplicant without problems (this is on my mother's pc which runs Dapper. wpasupplicant isn't very user friendly but it's a powerful tool)

---

