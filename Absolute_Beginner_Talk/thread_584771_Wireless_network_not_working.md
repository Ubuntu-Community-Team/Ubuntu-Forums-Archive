---
title: "Wireless network not working"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by SlinkyPete on 2007-10-21
Hi there, 
I'm using ubuntu (7.10) for the first time ever. 
I am unable to connect to my wireless network, although I can see my home network.
I am not sure if my drivers are installed properly. How do I check to see what is wrong?
Please help

---

### Post by mikeyphi on 2007-10-21
> **SlinkyPete said:**
> Hi there, 
I'm using ubuntu (7.10) for the first time ever. 
I am unable to connect to my wireless network, although I can see my home network.
I am not sure if my drivers are installed properly. How do I check to see what is wrong?
Please help

Which Wireless Network card?
Is your home network through that card?
What network options do you see in Network Manager?

---

### Post by w7kmc on 2007-10-21
Hi,

I just now completed a fresh install of 7.10 and went through the wireless set-up here...last night...again...

If it does not work straight out of the box...then  you may need to use ndiswrapper to set it up.  You see, some wireless card manufactures do not have Linux drivers, but you can install ndiswrapper which will "wrap" around a windows  driver and run your Linux system.   Sounds complicated....but once you have the correct information  ie...the card model, manufacturer, and the drive in hand, it is a very simple process. 

If you are not sure what type of card you have then you can check by typing: lspci

at a command line to get started...or check you PC manufacturing website...

---

### Post by BaffledMollusc on 2007-10-21
> **SlinkyPete said:**
> Hi there, 
I'm using ubuntu (7.10) for the first time ever. 
I am unable to connect to my wireless network, although I can see my home network.
I am not sure if my drivers are installed properly. How do I check to see what is wrong?
Please help

Open a terminal window (Applications->Accessories->Terminal) and type "lspci" (without the quotes) and press enter. Then type "ifconfig" and press enter. 

Post the output of both these commands in this thread. That will help us find what's wrong.

---

### Post by SlinkyPete on 2007-10-21
laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:14.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 03)
00:14.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (rev 01)
00:15.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1b.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 50)
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1d.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:1d.1 Modem: ALi Corporation M5457 AC'97 Modem Controller (rev 20)
00:1e.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 31)
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:D0:90:42:A2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:10:60:65:ED:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-10-60-65-ED-26-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



All right, hope you can make this work

---

### Post by SlinkyPete on 2007-10-21
I have the windows .inf and .sys files, but am unsure what to do next. Have installed ndiswrapper via the synaptic package manager but do not have the System>Administration>Windows Wireless Drivers option. Am I doing something wrong, or is this step not necessary?

Please help

---

### Post by w7kmc on 2007-10-21
Hi,
You can start the ndiswrapper gui from the command line like this:

gksu /usr/sbin/ndisgtk

Then select the correct .inf file in the gui....then configure your network from there as well

OR via command lines you can try these commands in succession:

sudo ndiswrapper -i your_inf_file.inf
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules 

I used the above commands to set the driver, and to ensure they get loaded boot time

You would replace the "your_inf_file.inf with the one you need...I also blacklisted the default driver by adding an entry to /etc/modprobe/blacklist

 blacklist bcm43xx

---

