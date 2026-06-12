---
title: "Cannot make internet work - Newbie"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Speck1965 on 2007-08-10
Just installed ubuntu 7.04. This is my first ever play with anything other than MS windows so don't get techie on me, ha ha!
My computer is an Advent 7102 laptop with a Ralink wireless card built in. Install went well and the wireless card appears to be working, i.e it tells me in the top right corner that the wireless is connected at 80% etc. Problem is the internet will not work. Anyone know whats wrong?

I have the roaming mode box checked, if I uncheck it I lose the connection. I have WEP 128bit encryption and have entered in the details but still no joy.

If I connect it to a hard wired internet connection all works well.

PLEASE HELP!!

Carl

---

### Post by amazingtaters on 2007-08-10
try installing ndiswrapper, it may clear up your problems. ndiswrapper is gonna make windows wireless drivers work natively in Linux and put one to work for you. Also, could you tell me exactly what chipset you wireless driver is (aka is it RalinkRT2500 or some other?)

---

### Post by Speck1965 on 2007-08-10
I think the chipset is indeed RT2500 but as mentioned above it appears to be working?
Remember I said I was a newbie? Well I got this  NDISwrapper program but how do I install it? No setup to double click on?

Carl

---

### Post by Austin_KW on 2007-08-10
You should not need ndiswrapper for the a Ralink chipsets. Open a terminal and post the output from "lspci". It is probably a rt2500 or  rt61 which have native drivers available. If the driver is already installed you may already have a ra0 network interface. Also post the output of "ifconfig -a". The ralink drivers do not wok well with network manager and it is best to configure them thru /etc/network/interfaces file. 
Post the output from the above commands and we can tell you how to get it working

---

### Post by lgambett on 2007-08-10
Before installing ndiswrapper please enter a terminal window and submit the following command,
*ifconfig*
then post the result here.
From your post it is not clear if you have a network or an Internet connection problem, so we will first try to determine this.

---

### Post by Austin_KW on 2007-08-10
> **Speck1965 said:**
> I think the chipset is indeed RT2500 but as mentioned above it appears to be working?
Remember I said I was a newbie? Well I got this  NDISwrapper program but how do I install it? No setup to double click on?

Carl
If it is the rt2500, you should have an ra0 interface. Configure it by editing the interfaces file; 
gksudo gedit /etc/network/interfaces

To configure for WPA; Change the ra0 entry in /etc/network/interfaces as follows (replacing YourESSIDhere and YourKey as appropriate)

```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid YourESSIDhere
    pre-up iwpriv ra0 set EncrypType=TKIP
    pre-up iwpriv ra0 set AuthMode=WPAPSK
    pre-up iwconfig ra0 essid YourESSIDhere
    pre-up iwpriv ra0 set  WPAPSK="YourWPAkeyHere"

```
To configure for WEP; Change the ra0 entry in /etc/network/interfaces as follows (replacing YourESSIDhere and YourKey as appropriate)
```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid YourESSIDhere
    pre-up iwconfig ra0 key YourWEPkeyHere

```

After making the change "sudo ifup --f ra0" should bring your wireless network up, It should then automatically come up on boot

---

### Post by Speck1965 on 2007-08-10
You are all way over my head, please assume you are dealing with a complete idiot and you won't be far wrong. I am sitting here with two laptops, this one with Windows XP so that I can post to you guys, and the other one with ibuntu on that is not on the internet.  I have tried to get that info you want (config etc) and have copied it to a pen drive but then I cannot post it as windows cannot open the files.

All the other info you have advised me to enter, where and how?

Thanks

---

### Post by lgambett on 2007-08-10
find the terminal program in the Ubuntu menus; it is like the MS/DOS prompt in Windows XP. Inside the terminal program enter the commands
*lspci*
and
*ifconfig*
You can copy / paste the output of the commands into OpenOffice, save it all as a .doc file and copy the file into the USB pen. Then you can transfer the file into the Win XP PC and post it into the forum.

---

### Post by Speck1965 on 2007-08-10
carl@carl-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:EC:0E:87:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10786 (10.5 KiB)  TX bytes:10786 (10.5 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0D:F0:1F:60:41  
          inet6 addr: fe80::20d:f0ff:fe1f:6041/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:348407 errors:2 dropped:2 overruns:0 carrier:0
          collisions:57 txqueuelen:1000 
          RX bytes:2307 (2.2 KiB)  TX bytes:15068554 (14.3 MiB)
          Interrupt:20 Base address:0x8000 

carl@carl-laptop:~$ 

HOWZAT?

---

### Post by lgambett on 2007-08-10
OK, now we are certain that your wireless card is not connected to the access point.
I can say that because no IP address was shown into the lspci command output.
Howewer the output of lspci is still missing. This command can help us identify exactly the network card you have.
You can post here the output of lspci, or try to apply immediately what was shown in post #6. In this post we are suggesting you to modify the file /etc/network/interfaces.
From your terminal you can do a safety copy of the file;
*sudo cp /etc/network/interfaces /etc/network/interfaces.old*
then modify the file according to the post #6 instructions
*sudo gedit /etc/network/interfaces*

---

### Post by Speck1965 on 2007-08-10
carl@carl-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
carl@carl-laptop:~$

---

### Post by Speck1965 on 2007-08-10
Going from bad to worse here. Carried out the advice posted @ No.6. Still no network, no internet and unable to get into the network or network tools, just get white boxes as if they part loaded then stopped?

Any suggestions?

---

### Post by mlsquad on 2007-08-10
From the cmd line type:
sudo iwconfig mode managed key *WEP_KEY*
sudo iwconfig ra0 essid "*YOUR_ESSID*"
sudo dhclient ra0

This should get your wireless card connected to your wireless network.  If you get any errors from dhclient let us know and report what you get from *ifconfig*

---

