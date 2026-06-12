---
title: "Questions on Wireless"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by wolfman89 on 2006-08-03
I have a Broadcom BCM4306 Wireless 802.11b/g adapter I have used it previously with Windows and it worked most of the time when my home network wasn't down. I am now unable to see my home network and I was wondering if it  is because the network is set up from Linksys or maybe it's because it was set up in Windows or if it's because it is encrypted by a WEP key I really don't know sorry if this question is stupid or redundant I just am trying to make my wireless work so I won't have a wire running from my room to the router acroos the house. Thanks for all help given bye!=D>

---

### Post by runim on 2006-08-03
I had the same problem, and I found that disabling encryption on your wireless solves it.  I disabled SSID broadcast and I called the network something really odd, so if 1 person is able to go through all the trouble to hack it, they deserve to borrow some wireless.  That personn probably has internet already though.

There are ways to get it to work with encryption, but I personally haven't done that yet.

---

### Post by benmoreassynt on 2006-08-03
@wolfman89

The Broadcom wireless cards/adaptors are notoriously tricky to set up with Ubuntu at first, but work very well once you have them up and running. Have you gone through the whole 'ndiswrapper' experience yet? It is sort of a rite of initiation to wireless Ubuntu.

I found the following thread to be far the best of a lot out there:

[http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

Good luck

ben

---

### Post by WADemosthenes on 2006-08-03
I beleive it's  because ubuntu install during installation, but then can't run them afterwards .  So when you try to install it using ndiswrapper ubuntu is already trying to run it... and it's just a mess.  Usually you can just blacklist the module or something... I actually just kept my card out of the computer when installing (so ubuntu didn't try to install drivers for it) and then ndiswrappered it.  It works fine now.  This might not be your problem though.  Try ndiswrapper, then work from there.

edit: ndiswrapper not working?  [http://www.ubuntuforums.org/showthread.php?t=201902&highlight=wademosthenes](http://www.ubuntuforums.org/showthread.php?t=201902&highlight=wademosthenes)

---

### Post by TFX360 on 2006-08-04
> **wolfman89 said:**
> I have a Broadcom BCM4306 Wireless 802.11b/g adapter I have used it previously with Windows and it worked most of the time when my home network wasn't down. I am now unable to see my home network and I was wondering if it  is because the network is set up from Linksys or maybe it's because it was set up in Windows or if it's because it is encrypted by a WEP key I really don't know sorry if this question is stupid or redundant I just am trying to make my wireless work so I won't have a wire running from my room to the router acroos the house. Thanks for all help given bye!=D>


The Linksys does not work in Linux automatically because the firmware isn't open source. They (read: Linksys doesn't) don't make drivers for it.

When using ndiswrapper from the repositories or not don't forget to blacklist bcm43xx.

```
 echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 
```

You can't use this driver when using ndiswrapper with windows drivers.

I have it working here. The network comes back with wpa_supplicant after Hibernating/Suspending.

Fist check if after installing and blacklisting:

```
 ndiswrapper -l 
```

It should say:

Driver present, Hardware present.

Good luck!


TFX

---

### Post by wolfman89 on 2006-08-04
OK it is me again I have downloaded the Wireless LAN client and now I can see the NEtwork, I can configure it, BUT, I believe one of the main problems that won't let me connect is the fact that the router and network itself are set up by LINKSYS and the LINKSYS router needs a WEP key AND a router password and I think the problem is that the WLAN client is giving the router the WEP Key and then the router asks for the router password and the client chokes on it because it doesn't have the router password in it's setting , there is no place in settings to even PUT a router password. SO if anyone could suggest or tell me how to perhaps EDIT the applet? or otherwise mess with the app so it will add a ROUTER PASSWORD to it's settings so when it goes to the router it will have both the WEP and Router Pass. Thanbks for all the replies ! :)

---

### Post by stormblue on 2006-08-04
Do you mean the password you type in when you go to "http://192.168.0.1" or is 192.168.1.1 for linksys.  I'm not sure?  Either way you shouldn't need that password.

---

### Post by wolfman89 on 2006-08-04
When you run thw Irreless Lan client It asks you for the WEP Key but Linksys ALSO has a router passsword when you run the WLAN util in WIndows it asks for the WEP AND the ROUTER PASSWORD and I THINK thats y the Wireless client app I have isn't connecting me to the network

---

### Post by TFX360 on 2006-08-04
> **wolfman89 said:**
> When you run thw Irreless Lan client It asks you for the WEP Key but Linksys ALSO has a router passsword when you run the WLAN util in WIndows it asks for the WEP AND the ROUTER PASSWORD and I THINK thats y the Wireless client app I have isn't connecting me to the network

Jibberish, can't make heads not tails of it. Wireless LAN client? Never heard of it. Are you using ndiswrapper? And maybe Gnome Network Manager?

Please post the outputs of:

```


lspci

iwconfig

ifconfig

ndiswrapper -l

sudo less /etc/network/interface

sudo grep 'bcm43xx' /etc/modprobe.d/blacklist

sudo grep 'ndiswrapper' /etc/modules


```

Kind regards,


TFX

---

### Post by wolfman89 on 2006-08-08
TFX,
 ok I'll show the difference between when I LAN connect the router and then when I try to wireless connect

LSPCI: 
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:09.0 Communication controller: Agere Systems: Unknown device 0620
0000:02:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

iw config:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:15:F2:A9:F5:49
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fea9:f549/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1066769 (1.0 MiB)  TX bytes:152418 (148.8 KiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
utility invalid driver!

sudo less /etc/network/interface:
/etc/network/interface: No such file or directory

sudo grep 'bcm43xx' /etc/modprobe.d/blacklist:
blacklist bcm43xx

sudo grep 'ndiswrapper' /etc/modules:
(nothing)

and here without the LAN connection:

lspci :
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:02:09.0 Communication controller: Agere Systems: Unknown device 0620
0000:02:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

iwconfig :
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ifconfig :
eth0      Link encap:Ethernet  HWaddr 00:15:F2:A9:F5:49
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ndiswrapper -l :
Installed ndis drivers:
bcmwl5  invalid driver!
utility invalid driver!

sudo less /etc/network/interface :
/etc/network/interface: No such file or directory

sudo grep 'bcm43xx' /etc/modprobe.d/blacklist :
blacklist bcm43xx

sudo grep 'ndiswrapper' /etc/modules:
(nothing)

that's all of what you asked for hope it helps!

G

---

### Post by chopper81 on 2006-08-08
I am sorry to barge in like this but I have almost the exact same problems that you do. My wireless and ethernet work at school but not at home. Have you had any luck in setting yours up? I am using the same card and also a linksys wireless router in my home network. If you could provide me with any suggestions that would be great.
chopper81

---

### Post by ripple on 2006-08-08
Hi, Im quite a bnoob here, well since about 1999 i have not used linux.  I have the same BCM4306 card.  I have tried numerous things.  I have tried the "bcm43xx" solution with windows drivers sys, and wl_apsta2.o files, no luck.  I am trying to sort out the details of the ndiswrapper solution.  Am i correct in asumming that the older versions came with NDIS but now require them to be installed separately?  You mentioned that you did get your card recognized.  Was this as ETH01 or WLAN01?  Right now I can activate the card in system>network but do nothing more.  The Network Manager does not recognize any cards.  Well i now that you know where im at, what did you finally use as a solution?  

Thanks in advance
Joe

p.s. i sure would like to get this working and be albed to say that linux is worth the effort!!

---

### Post by TFX360 on 2006-08-09
TFX,

ok I'll show the difference between when I LAN connect the router and then when I try to wireless connect

LSPCI: 

0000:02:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

**This confirms the hardware for us.**

iw config:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

**Not sure but I think we should be seeing different.**

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:15:F2:A9:F5:49
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fea9:f549/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1066769 (1.0 MiB)  TX bytes:152418 (148.8 KiB)
          Interrupt:209
[B]
This is your wired network I presume. This should not interfere with the wireless network anyways.
[/B]

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

**Local loopback, okay**

ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
utility invalid driver!

**What is te version of your card? Is it a Linksys? If so when it is a version 1.2 you MUST use the version 2 drivers from linksys!!! Let me know what version you have.**

sudo less /etc/network/interface:
/etc/network/interface: No such file or directory

*My mistake it should be sudo less /etc/network/interface**s***

sudo grep 'bcm43xx' /etc/modprobe.d/blacklist:
blacklist bcm43xx

**Very good, this confirms that the original driver module is blacklisted.**

sudo grep 'ndiswrapper' /etc/modules:
(nothing)

**This is probably because the driver is incorrect.**

that's all of what you asked for hope it helps!

I hope it helps you :D


G

---

### Post by TFX360 on 2006-08-09
> **chopper81 said:**
> I am sorry to barge in like this but I have almost the exact same problems that you do. My wireless and ethernet work at school but not at home. Have you had any luck in setting yours up? I am using the same card and also a linksys wireless router in my home network. If you could provide me with any suggestions that would be great.
chopper81

Works like a charm here, with wpa_supplicant for WPA Encryption. Even after hibernate and suspend, it works like a charm :)

Gimme the output of:

```

lspci | grep Broadcom

iwconfig

ifconfig

ndiswrapper -l

sudo less /etc/network/interfaces

sudo grep 'bcm43xx' /etc/modprobe.d/blacklist

sudo grep 'ndiswrapper' /etc/modules

```

---

### Post by TFX360 on 2006-08-09
> **ripple said:**
> Hi, Im quite a bnoob here, well since about 1999 i have not used linux.  I have the same BCM4306 card.  I have tried numerous things.  I have tried the "bcm43xx" solution with windows drivers sys, and wl_apsta2.o files, no luck.  I am trying to sort out the details of the ndiswrapper solution.  Am i correct in asumming that the older versions came with NDIS but now require them to be installed separately?  You mentioned that you did get your card recognized.  Was this as ETH01 or WLAN01?  Right now I can activate the card in system>network but do nothing more.  The Network Manager does not recognize any cards.  Well i now that you know where im at, what did you finally use as a solution?  

Thanks in advance
Joe

p.s. i sure would like to get this working and be albed to say that linux is worth the effort!!

My wireless in Ubuntu is eth0, wierd ehj! But still it works. wlan0 is not used. As far as I know. My card isn't recognized by the (Gnome) Network Manager too.

Gimme the output of:

```

lspci | grep Broadcom

iwconfig

ifconfig

ndiswrapper -l

sudo less /etc/network/interfaces

sudo grep 'bcm43xx' /etc/modprobe.d/blacklist

sudo grep 'ndiswrapper' /etc/modules

```

---

### Post by TFX360 on 2006-08-09
Guys,


I added this script for easy creating of the output.

It generates what I need to help you to output.txt.

You can paste this output in this thread.

Copy the file to you home directory or where ever you want.

The file -> [ATTACH]14064[/ATTACH]

and do:
```

sudo chmod +x broadcom.txt; ./broadcom.txt

```

Copy and paste the contents of output.txt here in the forum. Gedit starts automatically showing you the output.txt. Copy & Paste! :D


Kind regards,


TFX.

---

### Post by insyzygy on 2006-08-09
Ah, those lovely folks at broadcom, lets thank them for their wonderful attitude towards open source. The broadcom situation is probably the worst possible situation, you have two mutually conflicting solutions neither of which can be made to work out the box due to legal crap. 

Anyway. I have a dell with a truemobile card that uses the bcm43xx chipset.
I have it working with both ndiswrapper and bcm43xx (not at the same time of course). I found the bcm43xx was easier to set up. For me the best info for the bcm43xx is  this wiki,it has good instructions.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")
Note that the bcm43xx-fwcutter has a script that will do all the extraction for you from the correct file.  If you are trying the ndiswrapper solution you must look at 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page")
They have a list of devices and the correct driver for each. I found that if I used the correct driver but from a different source ndiswapper would report everything fine but the card wouldn't work. Similarly If I used the firmware cutter script and extracted it myself from the correct file but not the exact version it wanted, I got errors.

Note that if you want to experiment with both simultaneously you can load  the modules by 
```
sudo modprobe ndiswrapper 
```
or
```
 sudo modprobe bcm43xx
```


and unload them by 
```
sudo rmmod bcm43xx
```
or 
```
sudo rmmod ndiswrapper
```
To check which one is loaded at a given time do 
```
lsmod | grep ndiswrapper 
```
or ```
lsmod | grep bcm43xx
```

---

### Post by TFX360 on 2006-08-12
>  Guys,


I added this script for easy creating of the output.

It generates what I need to help you to output.txt.

You can paste this output in this thread.

Copy the file to you home directory or where ever you want.

The file -> broadcom.txt

and do:
Code:

sudo chmod +x broadcom.txt; ./broadcom.txt


Copy and paste the contents of output.txt here in the forum. Gedit starts automatically showing you the output.txt. Copy & Paste!


Kind regards,


TFX.



Well, I guess you guys solved it all. Would you mind to let us know?


Kind regards,


TFX

---

### Post by wolfman89 on 2006-08-26
Here's the info:

Broadcom card PCI version 2.2
-------------------------------
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
----------------------
how can I get the correct driver to fix the ndiswrapper issue?



> **TFX360 said:**
> TFX,

ok I'll show the difference between when I LAN connect the router and then when I try to wireless connect

LSPCI: 

0000:02:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

**This confirms the hardware for us.**

iw config:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

**Not sure but I think we should be seeing different.**

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:15:F2:A9:F5:49
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fea9:f549/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1066769 (1.0 MiB)  TX bytes:152418 (148.8 KiB)
          Interrupt:209
[B]
This is your wired network I presume. This should not interfere with the wireless network anyways.
[/B]

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

**Local loopback, okay**

ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
utility invalid driver!

**What is te version of your card? Is it a Linksys? If so when it is a version 1.2 you MUST use the version 2 drivers from linksys!!! Let me know what version you have.**

sudo less /etc/network/interface:
/etc/network/interface: No such file or directory

*My mistake it should be sudo less /etc/network/interface**s***

sudo grep 'bcm43xx' /etc/modprobe.d/blacklist:
blacklist bcm43xx

**Very good, this confirms that the original driver module is blacklisted.**

sudo grep 'ndiswrapper' /etc/modules:
(nothing)

**This is probably because the driver is incorrect.**

that's all of what you asked for hope it helps!

I hope it helps you :D


G

---

### Post by TFX360 on 2006-08-26
Look at post 16. Follow the instructions and paste the data here. Then I can help you further.

2.2 should be driver version 2.


Did you follow the instructions in the posts?

sudo modprobe ndiswrapper

Should start it automatically at startup

and you should have added ndiswrapper to /etc/modules


Kind regards,


TFX

---

