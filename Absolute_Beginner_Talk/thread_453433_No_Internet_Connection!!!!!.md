---
title: "No Internet Connection!!!!!"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-05-24
I dont know what the problem is but I keep losing my internet connection altogether.  
I have a wireless connection with a Linksys wmp54g PCI card 
In addition to that I also have it hardwired through a LAN connection and I keep losing both connections
Can anyone help me with this?

---

### Post by jrandolph on 2007-05-24
Bump 
Please help

---

### Post by MeeMaw on 2007-05-24
So, you mean you have a wireless card AND a wired ethernet connection? I think yoiu have to designate which one you want to be using at any one time.... sometimes when you have the cable connected, the wireless conflicts with it and neither works. If you want to use the wireless, try disconnecting the cable.....
Also, do you have your wireless configured already? or is that what you are trying to do?

:)

---

### Post by jrandolph on 2007-05-24
I only have the wired connection plugged in when I cannot get the wireless to work

I have been trying to get this wireless thing figured out for some time now and I think i have it and then all of a sudden I dont

---

### Post by MeeMaw on 2007-05-24
OK,  what version of Ubuntu are you using, Feisty? (that's 7.04)

And what do you get when you do these commands (post them back here);

lspci

sudo iwconfig

so we can see some info.... I have a WMP54g but the chipset may be different in yours than mine.
Don't give up!!!!   :D

---

### Post by jrandolph on 2007-05-30
Sorry I have been away for a few days --

jacob@jacob:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]
05:00.1 Display controller: ATI Technologies Inc RV370 secondary [ATI Sapphire X550 Silent]
jacob@jacob:~$ 


jacob@jacob:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"Wilcox Lumber"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:14:BF:8C:AB:9D   
          Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:**********   Security mode:open
          Link Quality=83/100  Signal level=-59 dBm  Noise level:-193 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

jacob@jacob:~$

---

### Post by kernel tom on 2007-05-30
when u have a wired connection try the following

sudo dhclient eth0

if you can't get an IP address then something is wrong between linux and ur ethernet card

---

### Post by jrandolph on 2007-05-30
jacob@jacob:~$ sudo dhclient eth0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:31:5c:33:38
Sending on   LPF/eth0/00:17:31:5c:33:38
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.104 -- renewal in 33510 seconds.
jacob@jacob:~$ 


I am really trying everything I can to get this wireless connection to get up and keep going but everything I have tried has failed!!!

---

### Post by kernel tom on 2007-05-30
well now that you have an internet connection i would do the following

sudo apt-get install wlassistant

then run

sudo wlassistant

and see if it brings up wireless networks and they'll be easy to connect to

EDIT: if there are no connections, your wireless device might not be "turned on" to do so depends on the version of k/x/ubuntu you are running.  Most of the times it's where your control panel like menu is then under Network, make sure you "enable this connection"

---

### Post by jrandolph on 2007-05-30
What is -- Broadcast?

---

### Post by kernel tom on 2007-05-30
> **jrandolph said:**
> What is -- Broadcast?

where are you seeing this?

---

### Post by jrandolph on 2007-05-30
On the Wireless Assistant it is asking me for 

Broadcast --???

And 

Domain --??

I dont know what to put in for these two entrys

---

### Post by kernel tom on 2007-05-30
ok, never recieved those questions before

did u start the program by running

sudo wlassistant

if you did please post a screen shot when it prompts you for those

---

### Post by jrandolph on 2007-05-30
Yes I did start it with that --

It is asking for those when I am setting up the connection within the program

not in the terminal

---

### Post by kernel tom on 2007-05-30
I assumed it was asking for it in the graphical interface

if it's an unprotected wireless network and you click on it, it should walk you through the first time set up.

I'm looking into those to terms to see if i can figure anything out for u... is ur wireless network WEP/WPA/WPA2 protected? or no?

EDIT:: CHOOSE AUTOMATIC (DHCP) when configuring your connection, then it shouldn't ask you

---

### Post by jrandolph on 2007-05-30
WEP protected

---

### Post by kernel tom on 2007-05-30
ok, so do the following

sudo wlassistant

click on your network,
choose Automatic (DHCP)
then choose open or shared key, not sure which one
enter ur key, if it's hex just enter the key, if it's not then click the checkbox for ASCII
and your off and running.

if you don't know any of your keys and u used a passphrase on windows, simply log into your router using it's IP address and go to ur wireless information, and it should display 4 different key codes, and anyone should work

---

### Post by jrandolph on 2007-05-30
The IP I have is a static IP

---

### Post by kernel tom on 2007-05-30
then use the manual configuration

you can leave some fields blank

---

