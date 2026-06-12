---
title: "network interface not detected"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by vikraman on 2007-12-04
Hello, 

I am a new user and this is my first time at linux, I've installed Ubuntu Feisty Fawn just a week ago. My ethernet card is a RTL-8139D and works fine on Windows XP, but its not detected in Ubuntu. The supplied CD contains drivers for linux and winxp.
How to install the linux driver for ubuntu. or can I use the winxp driver for this also. Then how?

---

### Post by hyper_ch on 2007-12-04
are you sure it's not detected or is it just not activated? Please go to the network manager, maybe you just need to tick the checkbox for activating it.

---

### Post by GSF1200S on 2007-12-04
WOW! The disc COMES WITH a linux driver?! Thats awesome...

Please do as said above.. maybe its already working and you just need to select it..

If not, could you post the results of:

```
ifconfig
```

from a terminal...

---

### Post by vikraman on 2007-12-05
> **hyper_ch said:**
> are you sure it's not detected or is it just not activated? Please go to the network manager, maybe you just need to tick the checkbox for activating it.

I used ipconfig, ipconfig eth0, lspci and lspci -n in the console and the result is
v@v-desktop:~$ ifconfig
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0          inet6 addr: ::1/128 Scope:Host          UP LOOPBACK RUNNING  MTU:16436  Metric:1          RX packets:2 errors:0 dropped:0 overruns:0 frame:0          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0     collisions:0 txqueuelen:0    RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

v@v-desktop:~$ ifconfig eth0
eth0: error fetching interface information: Device not found

v@v-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:0a.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)

v@v-desktop:~$ lspci -n
00:00.0 0600: 8086:7120 (rev 03)
00:01.0 0300: 8086:7121 (rev 03)
00:1e.0 0604: 8086:2418 (rev 02)
00:1f.0 0601: 8086:2410 (rev 02)
00:1f.1 0101: 8086:2411 (rev 02)
00:1f.2 0c03: 8086:2412 (rev 02)
00:1f.5 0401: 8086:2415 (rev 02)
01:0a.0 0200: 1904:8139 (rev 01)
moreover when i unzip the linux driver file, there are three files extracted and in readme.txt, is says the driver is meant for linux kernel version 2.4.x/2.5.x only but my linus kernel version is 2.6.20-15-generic.even  if a linux driver matching my kernel version is found I am not able to complly and install the module since I am new to LINUX unless step by step instructions are given by the experts like u. thank u

---

### Post by vikraman on 2007-12-05
> **GSF1200S said:**
> WOW! The disc COMES WITH a linux driver?! Thats awesome...

Please do as said above.. maybe its already working and you just need to select it..

If not, could you post the results of:

```
ifconfig
```

from a terminal...

I used ipconfig, ipconfig eth0, lspci and lspci -n in the console and the result is

v@v-desktop:~$ ifconfig
lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0          inet6 addr: ::1/128 Scope:Host          UP LOOPBACK RUNNING  MTU:16436  Metric:1          RX packets:2 errors:0 dropped:0 overruns:0 frame:0          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0     collisions:0 txqueuelen:0    RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

v@v-desktop:~$ ifconfig eth0
eth0: error fetching interface information: Device not found

v@v-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:0a.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)

v@v-desktop:~$ lspci -n
00:00.0 0600: 8086:7120 (rev 03)
00:01.0 0300: 8086:7121 (rev 03)
00:1e.0 0604: 8086:2418 (rev 02)
00:1f.0 0601: 8086:2410 (rev 02)
00:1f.1 0101: 8086:2411 (rev 02)
00:1f.2 0c03: 8086:2412 (rev 02)
00:1f.5 0401: 8086:2415 (rev 02)
01:0a.0 0200: 1904:8139 (rev 01)

moreover when i unzip the linux driver file, there are three files extracted and in readme.txt, is says the driver is meant for linux kernel version 2.4.x/2.5.x only but my linus kernel version is 2.6.20-15-generic.even  if a linux driver matching my kernel version is found I am not able to complly and install the module since I am new to LINUX unless step by step instructions are given by the experts like u. thank u

---

### Post by GSF1200S on 2007-12-05
Ha! Im no expert now.. lets give the actual experts there due credit- lol..

Ok, please also post the contents of: 

```
gedit /etc/network/interfaces
``` 

ifconfig is saying that you dont have an ethernet interface. The drivers may actually be installed, but since the network interface isnt there, it wont make any difference. Odd.. Im guessing the ethernet wasnt hooked up when you installed? Also post the readme in a quote box and maybe i can help you get the drivers installed if thats necessary... Standby, im also going to have you post a file I cant remember at the moment...

**EDIT** If you could, please post the contents of:

```
gedit /etc/udev/rules.d/70-persistent-net.rules
``` (If youre on Gutsy Gibbon 7.10)

-or-

```
gedit /etc/iftab
``` (if you are on Feisty Fawn 7.04)

---

### Post by plucky on 2007-12-05
Hi Vikraman,

I had the same problem when I first installed Ubuntu,and did some research on the exact same module. If I remember correctly the module does not use the **realtek** chipset but emulates it,and there was no driver in ubuntu.I think i read somewhere that they were going to try to fix it in Gutsy,but I am now on Gutsy and it still doesn't work.I bought another Network card and I am using it now.

If you do find some drivers to use in linux I would be very interested.

Cheers Plucky

---

### Post by vikraman on 2007-12-05
I posted the contents as advised by you

```
gedit /etc/network/interfaces
``` 

> auto lo iface lo inet loopback 
auto eth0 iface eth0 inet dhcp
auto eth1 iface eth1 inet dhcp
auto eth2 iface eth2 inet dhcp
auto ath0 iface ath0 inet dhcp
auto wlan0 iface wlan0 inet dhcp

ifconfig is saying that you dont have an ethernet interface. The drivers may actually be installed, but since the network interface isnt there, it wont make any difference. Odd.. Im guessing the ethernet wasnt hooked up when you installed? Also post the readme in a quote box and maybe i can help you get the drivers installed if thats necessary... Standby, im also going to have you post a file I cant remember at the moment...

```
gedit /etc/iftab
``` (if you are on Feisty Fawn 7.04)[/QUOTE]

>    # This file assigns persistent names to network interfaces.
                 # See iftab(5) for syntax.

---

### Post by vikraman on 2007-12-23
Hi, the problem solved. I changed the LAN card and now I am able to get internet. but one problem in ubuntu 7.04, the firefox does not open web pages. it shows 'server not found'error. so I installed kubuntu where the konqurer is diplaying web pages correctly. thanks to all

---

