---
title: "Steps to configure wireless internet?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Raghu Hegde on 2008-03-06
Hi, I'm fairly new to Ubuntu. Can somebody tell me the steps needed to configure wireless internet in Ubuntu 7.10? There is a NETGEAR wireless modem in my apartment... I was able to connect to the internet in Windows quite easily, but Ubuntu is proving to be a bit tougher :)
Any replies?

---

### Post by Slipmyknot101 on 2008-03-06
Hi. If you are brand new to the Linux scene, and/or more particularly, the Ubuntu scene, welcome aboard. I'm certainly no expert and I don't know everything, but I can try to help because I've had to do this before on a couple of Linux boxes.

Anyways,

First, it would really help if you could list the following:
1. The manufacturer of the computer
2. All the known specs about the computer (don't go swimming for product manuals or anything just yet).
3. If you have a wireless card or wireless networking device installed in/on computer for which you are requesting support.
--
edit: also, it would help if you could open the terminal (located in Applications, Accessories) and type 
> iwconfig and post the results here.

also, it would help if you could open the terminal and type > ifconfig and also post those results.

also, could you list which version of Ubuntu you are currently using?

also, have you tried, or do you have the ability to try connecting to a non-wireless (lol...wired) connection in your current location? If not, perhaps there is a location close by?

Sincerely,
Trevor

---

### Post by Raghu Hegde on 2008-03-06
Ok here goes..

My machine is a Dell Vostro 1000 laptop.. a brief description of the system configuration would be - it's an AMD 64-bit processor with a 2 GB RAM and a 120 GB hard disk. It's got a Dell Wireless 1490 802.11 a/g card on it.
I'm staying in an apartment which has a wireless modem. I was able to connect to the internet using Windows by keying in a Wi-fi password which was given to me (it helped that Windows recognized the Wireless modem on it's own).

The Ubuntu that I'm using is 7.10 - Gutsy Gibbon. Hope this information was useful to you and thanks in advance for the help!

---

### Post by mikeyphi on 2008-03-06
> **Raghu Hegde said:**
> Hi, I'm fairly new to Ubuntu. Can somebody tell me the steps needed to configure wireless internet in Ubuntu 7.10? There is a NETGEAR wireless modem in my apartment... I was able to connect to the internet in Windows quite easily, but Ubuntu is proving to be a bit tougher :)
Any replies?

Try this:
Open System/Administration/Network
Enter your password as requested - you should then be presented with a window showing wireless; wired and modem.
Check the wireless box - highlight wireless - select properties. The wireless should be in Roaming mode, deselect by unticking.
you should then be able to select 'NETGEAR'  in the name box;
type of encryption in the password box;
enter the password code
Then select Automatic DHCP in the configuration box
Then click OK

You may have to reboot before the settings are effective.

Please post results or further errors

---

### Post by Raghu Hegde on 2008-03-06
I'm afraid the above steps are not working :( 

Not sure what the problem is, but ifconfig says Access Point = Invalid. Does that mean anything? Also whats the difference between a hexadecimal WEP and an ASCII WEP??
Please help!!

---

### Post by ferdostar on 2008-03-06
First you have to install you wireless card (if it isn't), than connect to your wireless connection. Check [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw") and [this]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") for more information about. Then, considering that you have Dell Wireless 1490 802.11 a/g card, you can take a look at [this]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") and [this thread]("http://ubuntuforums.org/showthread.php?t=297092&highlight=dell+1501") but you should change the Broadcom 1390 to 1490.
About the difference between a hexadecimal WEP and an ASCII WEP is simple, the hexadecimal refers to the base-16 number system, which consists of 16 unique symbols: the numbers 0 to 9 and the letters A to F and the ASCII represents characters as numbers, with each letter assigne a number from 0 to 127. All that for representing in characters in bits.
For example One ASCII Character is eight bits, One HEX Character is four bits; 40-or 64-bit ASCII WEP code has five characters, 40- or 64-bit HEX WEP code has 10 characters etc.

---

### Post by stchman on 2008-03-06
> **Raghu Hegde said:**
> Hi, I'm fairly new to Ubuntu. Can somebody tell me the steps needed to configure wireless internet in Ubuntu 7.10? There is a NETGEAR wireless modem in my apartment... I was able to connect to the internet in Windows quite easily, but Ubuntu is proving to be a bit tougher :)
Any replies?

Give us an lspci output from your terminal.  We need to know what chipset that wireless card uses.

It looks like the Dell 1490 card is a Broadcom card so you will need to do some special things to get it working.

Did you check the Restricted Drivers Manager?  Remember Broadcom sucks for Linux.  You can get an Intel 3945 off ebay for around $20.

---

### Post by mikeyphi on 2008-03-06
> **Raghu Hegde said:**
> I'm afraid the above steps are not working :( 

Not sure what the problem is, but ifconfig says Access Point = Invalid. Does that mean anything? Also whats the difference between a hexadecimal WEP and an ASCII WEP??
Please help!!

ASCII is normal keyboard language - usually called a pass-phrase, it is more easily remembered than:-
hexadecimal is code - usually derived from the pass-phrase

---

### Post by thisismalhotra on 2008-03-06
> **Raghu Hegde said:**
> Hi, I'm fairly new to Ubuntu. Can somebody tell me the steps needed to configure wireless internet in Ubuntu 7.10? There is a NETGEAR wireless modem in my apartment... I was able to connect to the internet in Windows quite easily, but Ubuntu is proving to be a bit tougher :)
Any replies?

Goto terminal and run following\

```
lspci -v
```

Post the output pls...
We will surely be able to help??

---

### Post by Raghu Hegde on 2008-03-07
This is what lspci -v tells me..

~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
        Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
        Memory behind bridge: c0200000-c02fffff
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at 8438 [size=8]
        I/O ports at 8454 [size=4]
        I/O ports at 8430 [size=8]
        I/O ports at 8450 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at c0005000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0008000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0009000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
        Memory at c0004400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: Dell Unknown device 022a
        Flags: 66MHz, medium devsel
        I/O ports at 8410 [size=16]
        Memory at c0004800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8420 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Dell Unknown device 022a
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=08, subordinate=0a, sec-latency=64
        Memory behind bridge: c0300000-c03fffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 022a
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 10
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
        Subsystem: Dell Unknown device 0007
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 022a
        Flags: bus master, fast devsel, latency 64, IRQ 20
        Memory at c0300000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Dell Unknown device 022a
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at c0302800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
        Subsystem: Dell Unknown device 022a
        Flags: bus master, medium devsel, latency 0, IRQ 9
        Memory at c0302c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

raghoos@raghoos:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:09:AC:49:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
 
And this is what ifconfig says..

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:09:AC:49:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by rajaram_s on 2008-03-07
Hey...

I am also having a dell laptop but with an Intel wireless adapter. I have a Dell 640m series, but dont remember the wireless card's model, nor am i browsing from that computer now. I am using ubuntu 7.10. It is able to detect the networks present and also the signal strength, I assigned a static ip address configuration for the network too... but, when i ping other computers in the netowork, it says host unreachale.

---

### Post by Raghu Hegde on 2008-03-08
Hi all, I still haven't been able to complete the configuration :(

iwconfig gives me this output

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"SAPE183"  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can somebody help please?

---

### Post by mikeyphi on 2008-03-08
Broadcom - problematic!!

You will need a wired Intenet connection to install the necessary driver.
Open Restricted Drivers Manager and install drivers. It should get you to install a package called bcm43xx-fwcutter, with details of what to do next.

Get back to us if you have problems installing the Broadcom driver.

---

### Post by Raghu Hegde on 2008-03-08
Downloaded and installed the package.. what next?

---

### Post by mikeyphi on 2008-03-08
> **Raghu Hegde said:**
> Downloaded and installed the package.. what next?

Have you opened Restricted Drivers Manager and checked the box alongside Broadcom?
If yes - system should work after reboot.

---

### Post by Raghu Hegde on 2008-03-08
Yes... it is done but it's still not working... in fact I'm not even getting the wireless network in the system taskbar

---

### Post by sonichedgehog on 2008-03-08
I'm new to this forum altho some experience with Debian, watching this thread with interest as I'm hoping to get a friend's netgear adapter connected  next time I visit. I rebuilt his box using wired adapter, connecting as eth0.

The following may be helpful? I've been looking at:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)
5.2.2. from the contents includes:
In Debian / Ubuntu systems configuration requires the addition of a valid wireless-essid parameter to the /etc/network/interfaces file (etc....)

and I have also downloaded the Linux driver from netgear- but I don't know whether to try installing it, or configuring as directed in the howto- or whether I should do both? Suggestion most welcome, in any case I'll be interested to note how the problem posed in this thread progresses. Great forum!-Phil

---

