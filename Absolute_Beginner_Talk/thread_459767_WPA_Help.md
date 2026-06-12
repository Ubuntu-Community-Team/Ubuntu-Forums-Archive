---
title: "WPA Help"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by llamaaway on 2007-05-31
I'm a novice Linux user, I run 7.04 Feisty Ubuntu on an HP Pavillion DV5000 notebook and the wireless card shows up but I can't connect to anything. My router is a Belkin 54g with WPA encryption. How can I get this to work. Whenever I go to the top right network monitor/button I go to "connect to other wireless network" and enter all the information correctly. As soon as I'm done it says the network name I just entered and 0% connection. Also under Wireless Network  I see no networks! All help is appreciated! I know how to use the Terminal so anything you need just ask. 
Thanks!

---

### Post by Kobalt on 2007-05-31
Can you give us more information about your wireless card (you may need to set it up before you can connect wirelessly) ? If you don't know, please post here the output of the following command line : ```
lspci
```

---

### Post by oscar44 on 2007-05-31
Im using ubuntu feisty.
I have a bcm4318 wifi card.
I can not seem to get it to use wpa.
ive followed several documents, and now im lost.
Can anyone help?

---

### Post by oscar44 on 2007-05-31
Also, I have installed wpa_gui, and added the wpa supplicant that way, but this attempt also failed.
Prior to this i ran:

sudo apt-get install wpasupplicant
this worked.
sudo gedit /etc/wpa_supplicant.conf
Not sure what to put in here.

---

### Post by llamaaway on 2007-05-31
andrew@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by llamaaway on 2007-05-31
bump

---

### Post by kernel tom on 2007-05-31
ha calm down with the bumping...

do you have another means of conecting to the internet? the easy thing to do would be to download and install the WPA gui and go from there.  If not... 

you have to create a file called wpa_supplicant.conf
this will contain the vitals of ur network, authentication type, user name, and password

[http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA](http://ubuntuforums.org/showthread.php?t=202834&highlight=WPA)

that thread should be a lot of help

---

### Post by llamaaway on 2007-05-31
im on a wired connection right now, I'll check that out, thanks

EDIT: I jsut went into the manual config menu and wireless is not showing up anymore and  I get this from iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Kobalt on 2007-05-31
You should first set up the drivers for your card, so that it can work properly, before setting up WPA. Here is [how to set up your your BCM4318]("http://ubuntuforums.org/showthread.php?t=197102").

---

### Post by llamaaway on 2007-05-31
thanks alot for that how-to, I bookmarked it for future reference! It worked my wireless is recognized again but how can I connect my network. Also, my wireless light on my notebook is not on.

---

### Post by Kobalt on 2007-05-31
Make sure the wifi switch, if you have one, is on the 'On' position. 
To connect to your network you should only need to click on the network icon and select your network. You'll be asked your WPA key, and that should be it.

---

### Post by kernel tom on 2007-05-31
> **llamaaway said:**
> thanks alot for that how-to, I bookmarked it for future reference! It worked my wireless is recognized again but how can I connect my network. Also, my wireless light on my notebook is not on.

another thing could be that when u installed the drivers when u were wired, that it put the wireless card in the off position, cause you were already connected

go into your Network Settings, and make sure ur wireless card device is "enabled"

---

### Post by llamaaway on 2007-05-31
it says roaming mode enabled I can't find an enable button. And thanks so much for both of your help

---

### Post by Kobalt on 2007-05-31
Can you please post the output of the command line ```
iwconfig
```What happens when you click on the network icon in the top right corner of your screen ? Do you see a list of available networks ?

---

### Post by llamaaway on 2007-05-31
i see no available networks under Wireless Networks
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Kobalt on 2007-05-31
Did you edit the /etc/network/interfaces file, as someone suggested you in an earlier post about WPA ? You should only keep in this file this section : > auto lo
iface lo inet loopback
Any other thing you should see you have to put a # at the beginning of the line.

---

### Post by llamaaway on 2007-05-31
yeah those are the only things without a # sign in front of them

---

### Post by Kobalt on 2007-05-31
I see your wireless interface is labeled as eth1, this can be a problem for Network Manager. Try this : ```
sudo gedit /etc/iftab
```Add a # at the beginning of the eth1 line. Then run ```
sudo ndiswrapper -l
sudo ndiswrapper -m
```
I hope you can see the networks after this. You can also try a little reboot to get this going on...

---

### Post by llamaaway on 2007-05-31
after i did that, no networks still but i'll reboot and see what happens

---

### Post by llamaaway on 2007-05-31
Ubuntu died, I'm using Windows to post this. After I rebooted It got to about 1 and a half of tose little loading bars at the loadin screen then it waited then died. I orget what it said though. If I can't fix it I will be sorry to go back to XP

---

### Post by kernel tom on 2007-05-31
i'd do a fresh install from ur live CD, without plugging in ur ethernet cable, the Live CD should recognize ur wireless device, then u shouldn't have any problems 

but there may be a way to fix this without doing so, i just dont know it

---

### Post by llamaaway on 2007-05-31
k I'll try that

---

### Post by kernel tom on 2007-05-31
now after u install it then reboot without the cd you gotta go to ur network settings

go to Network Settings

enable ur wireless connections, and enter the name of ur network....

or download a program like wlassistant

sudo apt-get install wlassistant

and run it with the sudo comand

sudo wlassistant

should find all your networks and "walk" you thru the set up to ur network

---

### Post by llamaaway on 2007-05-31
still dead i think ill keep on trying to get it alive then ill try what you said! thanks!

---

### Post by llamaaway on 2007-05-31
tried everything, ubuntu has died :'( thanks lots for all your guys help

---

