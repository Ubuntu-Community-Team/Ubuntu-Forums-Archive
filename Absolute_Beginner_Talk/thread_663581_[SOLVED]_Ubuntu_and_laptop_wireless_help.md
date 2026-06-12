---
title: "[SOLVED] Ubuntu and laptop wireless help"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by huntis619 on 2008-01-10
Hi all. I'm new to the ubuntu experience.So far I am pleased with ubuntu. The only problem I'm having is connecting to the internet with my laptop. For the past 3 days I have been reading different posts on the situation.It seems though most of the info is for wireless aftermarket cards. Mine is built in to the laptop. I have a hp zv5410us and a belkin F5D8230-4 wireless router. Please in order to move on I need my wireless to work, so PLEASE can someone help me. Also Ive been windozed for a while. So please be patient with me.

---

### Post by NullHead on 2008-01-10
Did you use the Restricted Drivers manager under the menu system>administration? and did it work?

---

### Post by huntis619 on 2008-01-10
I did do that but the wireless is still not working. Hereis some more info.

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Steven"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Rog-Mahal on 2008-01-10
Well, it looks like your card is recognized. Do you have the correct password entered under your network settings? Have you tried doing th following commands in terminal:

```
sudo ifdown eth1
```

```
sudo ifup eth1
```

That should disconnect and then reconnect your wireless to the router. 

Hope that helps.

---

### Post by Digger78 on 2008-01-10
post output from

```
iwlist scan
```

---

### Post by huntis619 on 2008-01-10
OK I'll try it and let you know the results. Currently looking online for 100 ft. ethernet cables. UGHH

---

### Post by huntis619 on 2008-01-10
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:A8:0C:B4
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=94/100  Signal level=-47 dBm  Noise level=-66 dBm
                    Extra: Last beacon: 412ms ago

---

### Post by huntis619 on 2008-01-10
sudo ifdown ethl
ifdown: interface ethl not configured
steven@steven-laptop:~$ sudo ifup ethl
Ignoring unknown interface ethl=ethl.

---

### Post by Digger78 on 2008-01-10
i'm guessing that is not your access point?

although its a strong signal to be a nieghbours.

can you check your routers essid.

---

### Post by Digger78 on 2008-01-10
> **huntis619 said:**
> sudo ifdown ethl
ifdown: interface ethl not configured
steven@steven-laptop:~$ sudo ifup ethl
Ignoring unknown interface ethl=ethl.

**eth1** not ethl

---

### Post by huntis619 on 2008-01-10
sudo ifdown eth1
[sudo] password for steven:
There is already a pid file /var/run/dhclient.eth1.pid with pid 5351
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:a8:c7:7e
Sending on   LPF/eth1/00:90:4b:a8:c7:7e
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.2.1 port 67
steven@steven-laptop:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:90:4b:a8:c7:7e
Sending on   LPF/eth1/00:90:4b:a8:c7:7e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
steven@steven-laptop:~$

---

### Post by Digger78 on 2008-01-10
Did you check your router to see what essid it is broadcasting?

---

### Post by huntis619 on 2008-01-10
my SSID is Belkin_Pre-N_611414

---

### Post by huntis619 on 2008-01-10
I'm sorry, what is a essid?

---

### Post by Digger78 on 2008-01-10
same thing ;-)

how close to the router are you?

 if your in another room, take your laptop and sit next to the router then try** iwlist scan**

---

### Post by Digger78 on 2008-01-10
can you post the outputs from

```
lspci
```

```
lshw -C network
```

---

### Post by huntis619 on 2008-01-10
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:A8:0C:B4
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=93/100  Signal level=-52 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 248ms ago

steven@steven-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
steven@steven-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4c:8f:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.7 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:a8:c7:7e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

---

### Post by Digger78 on 2008-01-10
I think you should try these steps, it will use Ndiswrapper + windows driver instead of the native driver


**Instructions copied from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-818e0ccb34dc3e6733f798494fb6ce95ea5548c6") **

**This is not a script. You'll enter one line at a time*, and will individually respond to sudo password prompts, etc. *You can also copy and paste one line at a time: To copy from the browser, use ctrl-c, but to paste into the terminal (at least Gnome's), use ctrl-shift-v.**


**Step 1: All BCM43xx - Install NDISWrapper and Blacklist Native Driver**

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
```
sudo apt-get install ndiswrapper-utils-1.9
```
```
mkdir ~/bcm43xx; cd ~/bcm43xx
```


[B]Step 2: Download and Extract Drivers
[/B]
```
sudo apt-get install cabextract
```
```
wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
```
```
cabextract sp33008.exe
```

**Step 3: All BCM43xx - Configure NDISWrapper (and WPA Supplicant)**
```
sudo ndiswrapper -i bcmwl5.inf
```
```
ndiswrapper -l
```
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
```
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
```
```
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
```
```
sudo ndiswrapper -m
```
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

**Now, REBOOT.**

After rebooting, you should be able to click the network manager icon. (In Gnome, it looks like two black monitors overlapping each other on the top panel.) Hopefully, you'll see the available wireless access points under "Wireless Networks" and your machine ought to try to connect to one of them if you remove your network cable (or if you select one of them with a mouse click).

---

### Post by huntis619 on 2008-01-10
Here is the response


-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist                                                                                             sudo apt-get install ndiswrapper-utils-1.9                                                                                                                   mkdir ~/bcm43xx; cd ~/bcm43xx
[sudo] password for steven:
blacklist bcm43xx
bash: cd: /home/steven/bcm43xx: Not a directory
steven@steven-laptop:~$ sudo apt-get install cabextract                                                                                                                              wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)                                                                                                  cabextract sp33008.exe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wget is already the newest version.
E: Couldn't find package ftp:
steven@steven-laptop:~$ sudo ndiswrapper -i bcmwl5.inf                                                                                                                               ndiswrapper -l                                                                                                                                               sudo depmod -a                                                                                                                                               sudo modprobe ndiswrapper                                                                                                                                    sudo cp /etc/network/interfaces /etc/network/interfaces.orig                                                                                                 echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces                                                                               sudo ndiswrapper -m                                                                                                                                          echo 'ndiswrapper' | sudo tee -a /etc/modules                                                                                                                echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
[sudo] password for steven:[sudo] password for steven:
tee: invalid option -- m
Try `tee --help' for more information.
`tee --help'

Sorry, try again.
[sudo] password for steven:
steven@steven-laptop:~$ steven@steven-laptop:~$ sudo ndiswrapper -i bcmwl5.inf                                                                                                                               ndiswrapper -l                                                                                                                                               sudo depmod -a                                                                                                                                               sudo modprobe ndiswrapper                                                                                                                                    sudo cp /etc/network/interfaces /etc/network/interfaces.orig                                                                                                 echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces                                                                               sudo ndiswrapper -m                                                                                                                                          echo 'ndiswrapper' | sudo tee -a /etc/modules                                                                                                                echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
tee: invalid option -- m
Try `tee --help' for more information.

---

### Post by huntis619 on 2008-01-10
Now I Can't Even See My Wireless Connection Under Networks.

---

### Post by Digger78 on 2008-01-10
start again, this time copy and paste **1 line at a time**

[QUOTE=Digger78]This is not a script. **You'll enter one line at a time***, and will individually respond to sudo password prompts, etc. *You can also copy and paste one line at a time: To copy from the browser, use ctrl-c, but to paste into the terminal (at least Gnome's), use ctrl-shift-v.

[/QUOTE]

---

### Post by huntis619 on 2008-01-10
I tried it again and I still can't see my wireless connection when I open my network.

---

### Post by stchman on 2008-01-10
> **huntis619 said:**
> Hi all. I'm new to the ubuntu experience.So far I am pleased with ubuntu. The only problem I'm having is connecting to the internet with my laptop. For the past 3 days I have been reading different posts on the situation.It seems though most of the info is for wireless aftermarket cards. Mine is built in to the laptop. I have a hp zv5410us and a belkin F5D8230-4 wireless router. Please in order to move on I need my wireless to work, so PLEASE can someone help me. Also Ive been windozed for a while. So please be patient with me.

What model of wireless card does this laptop have.  HP laptops use either an Intel or a Broadcom wireless card.

---

### Post by Digger78 on 2008-01-10
Did you hit return after each line?

---

### Post by huntis619 on 2008-01-10
OK explain this to me. Copy one line, paste one line then enter or copy one line, paste one line identical the way you have it in each box then press enter. I copied it just the way you had it and now I can't see my wireless connection option when I open my network.

---

### Post by Digger78 on 2008-01-10
copy and paste 1 line then hit enter,  enter password if required, then wait for the prompt to return for the next command.

I edited my post above to hopefully make it easier to understand.

---

### Post by NullHead on 2008-01-10
Try ```
sudo rmmod bcm43xx && modprobe ndiswrapper
```

---

### Post by huntis619 on 2008-01-10
Thank you, thank you thank you thank you   Digger78. It worked just like you said.

---

### Post by Digger78 on 2008-01-10
NP,  ;)

 i'm glad i could help. :D

Dont forget to mark this thread as solved.  (thread tools)

---

### Post by huntis619 on 2008-01-10
Hi all. I just wanted to say thank you to everyone who helped me to get started with ubuntu. Thank you for your time, patience and understanding. I have nothing but love for you. A special thanks to oldos2er and shareMenaPeace for helping me with my drivers and Digger78 for solving my problem with my wireless networking. In the future I hope I can be the same help to someone else. Installed ubuntu 7.10  on Sunday (1/06/08) and by Thursday (1/10/08) I have all my drivers and networking configured. I'm so happy, I really like ubuntu   THANK YOU ALL AGAIN.

---

### Post by iceman0304 on 2008-01-10
I tried to do the same thing but had no luck, I'm having the same problem, did the lines lost my wireless network, 

using a Compaq with the Broadcom 4306 chipset

I'm a newbie when it comes to installing anything via terminal as to where the file should be downloaded to?, where the file should be placed?, which directory I should be in when install?  

Been trying to figure linux out for the past few years when I have time, and that comes and goes..

Hopefully I can be helped out like this user was, lack of wireless network is what keeps me  away from linux.

---

### Post by Digger78 on 2008-01-10
can you post the outputs from
```

lspci
```
and
```
lshw -C network
```

---

### Post by iceman0304 on 2008-01-10
I notice it has become unclaimed


WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:81:0e:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 ip=192.168.1.112 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
matt@matt-laptop:~$

---

### Post by Digger78 on 2008-01-10
outputs from

```
lspci

```
```
cat /etc/modprobe.d/blacklist
```

---

### Post by iceman0304 on 2008-01-10
I added the last 2 lines to the blacklist like I thought it said on the one site

# drivers wireless ACX
blacklist acx


matt@matt-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
matt@matt-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx
blacklist bcm43xx

# drivers wireless ACX
blacklist acx
matt@matt-laptop:~$

---

### Post by Digger78 on 2008-01-10
OK you have the native driver blacklisted bcm43xx

So go through the commands i posted above, just copy and paste them into a terminal

Hit enter/return after each command, some commands will require your root password, wait for the prompt to return before pasting the next command

 start from

```
sudo apt-get install ndiswrapper-utils-1.9

```

if you receive any errors copy and paste the contents here.

---

### Post by iceman0304 on 2008-01-10
Step 1 fine

should I place the linux CD in the drive?

Step 2

matt@matt-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract
matt@matt-laptop:~/bcm43xx$

---

### Post by huntis619 on 2008-01-10
Hello all. Iceman0304 I was reading that you were having the same problem I was having. I forgot that I had the disc in the drive, I think thats what messed me up the first time I tried Digger78 solution. When I took the disc out and tried second time.....voila.

---

### Post by iceman0304 on 2008-01-10
I tried both ways and nothing has changed, when i started it wasn't in the drive, then after I  asked the question I tried with it in and still nothing.

---

### Post by Digger78 on 2008-01-10
ok, open **adept manager** and enable all repositories

adept menu > manage repositories

check all the boxes on each tab then close the window. 

it should ask about updating  blah blah blah. - click YES

put your CD in,

when adept is finished getting the updates you can close it.

continue through the steps starting from

sudo apt-get install cabextract

if you closed the terminal that you were using before, start with

```
cd ~/bcm43xx
```

---

### Post by iceman0304 on 2008-01-10
What and where is this? adept manager

---

### Post by Digger78 on 2008-01-10
sorry i have kubuntu, i forgot ubuntu has [B]synaptic package manager
[/B]

synaptic package manager > settings > repositories

select them all

click **reload**,

when it has the updates close synaptic

---

### Post by iceman0304 on 2008-01-10
I'm using "PSK2 Personal" does linux support this?

error marked below as    <-------------problem


matt@matt-laptop:~/bcm43xx$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
matt@matt-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
matt@matt-laptop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : invalid driver!                                                   <-----------------------problem 
matt@matt-laptop:~/bcm43xx$

---

### Post by Digger78 on 2008-01-10
i have no idea about PSK2 Personal

are you using a 64bit system?

OK just incase the installed version is wrong

```
sudo ndiswrapper -r bcmwl5
```

```
sudo ndiswrapper -i bcmwl5.inf
```

```
ndiswrapper -l
```

---

### Post by iceman0304 on 2008-01-10
32 bit system ver7.10


matt@matt-laptop:~/bcm43xx$ sudo ndiswrapper -r bcmwl5
[sudo] password for matt:
matt@matt-laptop:~/bcm43xx$ sudo ndiswrapper -r bcmwl5
couldn't delete /etc/ndiswrapper/bcmwl5: No such file or directory
matt@matt-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
matt@matt-laptop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
matt@matt-laptop:~/bcm43xx$

---

### Post by Digger78 on 2008-01-10
```
sudo rmmod ndiswrapper
```
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
```
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
```
```
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
```
```
sudo ndiswrapper -m
```
```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```
```
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Now, REBOOT.

**I would recommend disabling security temporarily on your router it will make it easier to verify that you can connect to the router**

After rebooting, you should be able to click the network manager icon. (In Gnome, it looks like two black monitors overlapping each other on the top panel.) Hopefully, you'll see the available wireless access points under "Wireless Networks" and your machine ought to try to connect to one of them if you remove your network cable (or if you select one of them with a mouse click).

---

### Post by iceman0304 on 2008-01-10
Does it matter witch directory I'm in to do this?


matt@matt-laptop:~/bcm43xx$ sudo rmmod ndiswrapper
[sudo] password for matt:
matt@matt-laptop:~/bcm43xx$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
matt@matt-laptop:~/bcm43xx$

---

### Post by Digger78 on 2008-01-10
Now that you have the driver installed, it doesnt matter which directory you are in

thats OK continue from

```
sudo depmod -a
```

---

### Post by NullHead on 2008-01-10
> **iceman0304 said:**
> Does it matter witch directory I'm in to do this?


matt@matt-laptop:~/bcm43xx$ sudo rmmod ndiswrapper
[sudo] password for matt:
matt@matt-laptop:~/bcm43xx$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
matt@matt-laptop:~/bcm43xx$

you only need to rmmod ndiswrapper once.

---

### Post by iceman0304 on 2008-01-10
I typed it twice cause I didn't see any response and wasn't sure if I was supposed to get one or not.


Ok I did have it working, but I had to turn off the security,  My router only supports WEP,PSK pers., PSK ent., PSK2 pers., PSK2 ent. no WPA..

Need to find out if ubuntu can support the PSK's


Thank you so much for all the help..

---

