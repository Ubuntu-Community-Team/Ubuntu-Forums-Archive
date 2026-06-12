---
title: "Still can't get connection with router"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Domino3 on 2007-08-22
When I try to connect to my wireless router with WEP encryption I enter the right key but it doesn't connect. How do you fix this?

---

### Post by Dr Small on 2007-08-22
Personally, if this was my case, I would connect to the router and remove the wep key to see if I could connect. If I could, I would then look for plausible possibilities of why the WEP key is not working.

Dr Small

---

### Post by Domino3 on 2007-08-22
I removed the WEP Key and it still does not work. I looked for Tutorials, tried them and they did not work.

---

### Post by WebSiteGuru on 2007-08-22
> **Domino3 said:**
> I removed the WEP Key and it still does not work. I looked for Tutorials, tried them and they did not work.

It's not the WEP key that giving you problem. Something else stopping you from doing that.

Can you show your ipconfig? Maybe something is missing in the configuration.

---

### Post by Domino3 on 2007-08-23
In Windows or Ubuntu?
When I install in Ubuntu I have to use my integrated graphics instead of my PCI. Why is this?

Windows IP Configuration


Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : gateway.2wire.net
        IP Address. . . . . . . . . . . . : 192.168.1.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.254

---

### Post by yogo on 2007-08-23
It is ifconfig in terminal not ipconfig as in windows.

HTH

---

### Post by dwhitney67 on 2007-08-23
What kind of router do you have?

As a previous post suggested, run this command from a terminal:

```
$ /sbin/ifconfig
```

and post the results.

Are you able to connect to your router using your web browser (e.g. Firefox)?

P.S.  Consider using WPA in lieu of WEP... it is more secure.

---

### Post by Domino3 on 2007-08-23
I have a 2Wire router.
Ok. Here they are.

ubuntu@ubuntu:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:2B:22:E0:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:2B:22:E0:AA  
          inet addr:169.254.7.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1432 (1.3 KiB)  TX bytes:1432 (1.3 KiB)

ra0       Link encap:Ethernet  HWaddr 00:12:17:83:81:DD  
          inet6 addr: fe80::212:17ff:fe83:81dd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:2448 (2.3 KiB)  TX bytes:172864 (168.8 KiB)
          Interrupt:17

And I am not able to connect to my router in Firefox.

---

### Post by schorsch on 2007-08-23
What is the output of the follwing commands:
```
iwconfig
lspci -v
sudo dhclient ra1
```
I would try to use a cabled connection to the router to connect there via firefox.

---

### Post by Saxone on 2007-08-24
Hi all,
I am being experiencing the same problem for a week. Before my wireless connection worked intermittently and slowly but now it is completely dead. I tried to reset my rooter but I can't connect (even via cable) to configure it on Ubuntu, so I tried on Windows and I could do it without any problems. But I can't still connect to the Internet via router, while direct connection works.

Very interested on your discussion.

---

### Post by Domino3 on 2007-08-24
> **schorsch said:**
> What is the output of the follwing commands:
```
iwconfig
lspci -v
sudo dhclient ra1
```
I would try to use a cabled connection to the router to connect there via firefox.

When I entered that i get:

ubuntu@ubuntu:~$ iwconfig lspci -v sudo dhclient ra1
Error : unrecognised wireless request "-v"
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-69 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, fast devsel, latency 0

00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03) (prog-if 00 [VGA])
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 10
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e8100000-e9ffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Intel Corporation 82801AA IDE
        Flags: bus master, medium devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 1080 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801AA USB
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 10a0 [size=32]

00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
        Subsystem: Intel Corporation 82801AA SMBus
        Flags: medium devsel, IRQ 9
        I/O ports at 1100 [size=16]

00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1200 [size=256]
        I/O ports at 1300 [size=64]

01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Trigem Computer Inc. Unknown device 7148
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at 2000 [size=256]
        Memory at e8100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
        Subsystem: Risq Modular Systems, Inc. Unknown device 044e
        Flags: medium devsel, IRQ 255
        Memory at e8100400 (32-bit, non-prefetchable) [disabled] [size=256]
        I/O ports at 2800 [disabled] [size=8]
        I/O ports at 2400 [disabled] [size=256]
        Capabilities: <access denied>

01:0d.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Linksys WMP54G 2.0 PCI Adapter
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at e8102000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

01:0e.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device b309
        Flags: 66MHz, medium devsel, IRQ 255
        Memory at e9000000 (32-bit, non-prefetchable) [disabled] [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [disabled] [size=128M]
        [virtual] Expansion ROM at e8120000 [disabled] [size=128K]
        Capabilities: <access denied>

ubuntu@ubuntu:~$ sudo dhclient ra1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ra1: ERROR while getting interface flags: No such device
ra1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

---

### Post by schorsch on 2007-08-24
Uhm, sorry, just a typo in my post before:
```
sudo dhclient ra0
```
It seems as if you are connected to your WLAN router as you get:
```
Link Quality=80/100 Signal level=-69 dBm Noise level:-192 dBm
```
... but the ESSID is "" ... empty ... weird ...

---

### Post by Domino3 on 2007-08-24
Maybe It's because ubuntu lets you enter your key as a passphrase instead of a WEP key because I remember on windows that on linsys monitor you enter a passphrase and it dechiphers them as different letters instead of the key. On linsys monitor you can enter a key at the bottom. One time I entered my key as a passphrase but it did not work. but as a key it did

---

### Post by QuantumFlux on 2007-08-24
I am having the same problem with a linksys router.  However neither typing in my WEP or the passphrase works.  It just keeps reading and reading and reading until it gives up.  I know it works because it worked in windows.

---

### Post by anewguy on 2007-08-25
Are you sure you got the pass key correct?  I have a 2WIRE  DSLModem/Wireless Router combination.  By default, this modem/router has a WEP pass key enabled so when reset it the WEP pass key is still enabled.  You have to connect to the modem at 192.168.1.254 in order to configure it and remove or change the pass key.  If you can't get to it wirelessly, then you need to hardwire it to do so.  By default, the WEP pass key is the 10 character code below the serial number on the modem/router.

I have network-manager-gnome installed, so when the wireless card itself is working, I click on the network manager icon on the top bar and it drops down a list of networks I can connect to.  Whenever I change something with the router I always go back and re-enter the passkey.  To do so, select WEP on the list, then select the 64-bit selection, then just enter the pass key from the bottom of the modem/router.  This has worked everytime for me with my 2WIRE product.:)

Edit:  Forgot to mention that the default session id from the 2WIRE modem/router I have is 2WIRExxx where xxx are the last 3 digits of the serial number.

---

### Post by Domino3 on 2007-08-25
I tried everything you said but it didn't work. Which 64-bit? acsi or hexadecimal. acsi doesn't let me login.

---

### Post by anewguy on 2007-08-25
> **Domino3 said:**
> I tried everything you said but it didn't work. Which 64-bit? acsi or hexadecimal. acsi doesn't let me login.

You want to use hexadecimal.:)

---

### Post by Domino3 on 2007-08-26
It still won't let me login with hexadecimal. The thing just keeps spinning but won't connect.

---

### Post by anewguy on 2007-08-27
Have you ever connected to the router with any computer and set things up in the router?  If so, did you change the default from WEP to WPA or change the default password?  What is the model of your router?

---

### Post by Domino3 on 2007-08-27
Yes, I have connected to it in windows on different computers and the model is 2700HG-B Gateway.
I have not ever changed the WEP to WPA or anything.
Have never changed default password.

---

### Post by anewguy on 2007-08-27
Well, my modem/router is 2701HG-B, so I think we are dealing with the same animal. So, let's try this one more time:

click on the network manager icon on the top bar

click on Connect to other wireless network

put in 2WIRExxx (where xxx is the last 3 digits of the serial number) as the network name

under the Wireless Security, click and select WEP 64/128 bit hex

click the Show key button

enter the 10 digit code under your serial number in the Key field

leave Authentication as Open System

click connect


If that doesn't work, please report back here with the result and what you had to enter in Windows to get Windows to connect (it requires the same type of setup information in order to connect to the router).

Good Luck!:)

---

### Post by Domino3 on 2007-08-27
It still doesn't work.
By the way, do you have a custom password?
Could it be my firewall on the router? It has a built in one.
I could configure the router to let ubuntu through my router. I just need to know which port ubuntu connects to.
Or should I use ubuntu 6.06 and see if it works?

---

### Post by anewguy on 2007-08-27
I never had a problem with the 2WIRE firewall - Ubuntu just worked through it as soon as I set the network key.  I have changed the modem/router config so that I do have my own password instead of the default (note to everyone - if you've got a router, be sure you've changed the default password on it).

Once I installed the wireless drivers, I have done the things mentioned to have mine working.  One thing that I have never been able to get working is WPA, so if you have that set, change it back to WEP (yeah, I know it's almost as good as no protection, but WPA hasn't ever worked on my router/modem under Windows or Linux).  

To just connect to the router for maintenance, I connect to 192.168.1.254 and use the password I have on my router.  If you have never set a password on the router, then you will need to use the default password.  To just connect to the internet, once I've set the network key I have had no problems - it just works.  I would check the configuration on one of the Windows computers you have used to connect, and then try to duplicate that in Ubuntu.  BTW - do your wireless settings (System/Administration/Network) show as "roaming"?  I was never able to get my wireless to connect trying to force it in that screen, so I set it to roaming and then went to network-manager-gnome to get things to work.

So, since I'm no expert, and I have exhausted what I do know, I guess you'll have to see if you can find someone else to help you.  Have you tried contacting 2WIRE to see what they say?

Sorry I can't be of more help to you, and best of luck!:)

---

### Post by Austin_KW on 2007-08-27
You need to modify the file  /etc/network/interfaces as follows. 
Use the comand "**gksudo gedit /etc/network/interfaces**" to edit the file
For WEP
```

auto ra0
iface ra0 inet dhcp
	pre-up ifconfig ra0 up
	pre-up iwconfig ra0 essid **YourESSID**
## Plus one of the following; depending if your WEP is HEX,a character String or OFF
	pre-up iwconfig ra0 key **YourWepKeyHex** 
or
	pre-up iwconfig ra0 key **s:YourWepKeyAscii**
or
        pre-up iwconfig ra0 key **OFF**

```

After you make the and save edits, enter the command "**sudo ifup --f ra0**" (note the double '-'). This command will force ra0 to come up using the changes.

---

### Post by Domino3 on 2007-08-28
> **Austin_KW said:**
> You need to modify the file  /etc/network/interfaces as follows. 
Use the comand "**gksudo gedit /etc/network/interfaces**" to edit the file
For WEP
```

auto ra0
iface ra0 inet dhcp
	pre-up ifconfig ra0 up
	pre-up iwconfig ra0 essid **YourESSID**
## Plus one of the following; depending if your WEP is HEX,a character String or OFF
	pre-up iwconfig ra0 key **YourWepKeyHex** 
or
	pre-up iwconfig ra0 key **s:YourWepKeyAscii**
or
        pre-up iwconfig ra0 key **OFF**

```

After you make the and save edits, enter the command "**sudo ifup --f ra0**" (note the double '-'). This command will force ra0 to come up using the changes.

I did that I got a lease and stuff but I noticed that i had no connection. So then I tried to connect to it but it didn't work. so then I modified the interface to find that it was empty. Then I did it and restarted but I couldn't boot ubuntu. So then I got rid if it.

---

