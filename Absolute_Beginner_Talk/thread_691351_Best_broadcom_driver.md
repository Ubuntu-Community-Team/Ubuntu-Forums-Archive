---
title: "Best broadcom driver???"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by whos2know on 2008-02-08
Hi, I'm kinda new to Ubuntu.  I have a Broadcom wifi card in my laptop.  I have successfully installed a driver that works with my system but its a bit slow.  How do I get a proper driver that will allow my wifi to run a bit faster.  Any info that I need to relay to you for help is no problem.  Just let me know what I have to do.  Thank you very much!!

Bobby

---

### Post by jan quark on 2008-02-08
run in terminal and post the output thx 
```
lspci
```

broadcom cards are fun to set up, I use one for myself but we will see and try to help

---

### Post by zsobin on 2008-02-08
I've almost always had better luck using windows drivers with ndiswrapper then using the linux native driver.  Find the inf file you used for your windows install.  It their is a cd that came with it, run the setup.exe, it will self extract into a temp directory.  Find just the driver inf file, use this with ndiswrapper.  There are many ndiswrapper forums.  If you don't have the cd, just type lspci, then for your card type type in "ndiswrapper my_card_type  gutsy"

---

### Post by whos2know on 2008-02-08
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
bobby@TheOne:~$ 


thank you for the quick reply!!

---

### Post by jan quark on 2008-02-08
native driver installation
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d_%28Native_Driver%29?highlight=%28BCM4318%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d_%28Native_Driver%29?highlight=%28BCM4318%29)

windows driver installation using the application ndiswrapper
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28BCM4318%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28BCM4318%29)

---

### Post by whos2know on 2008-02-08
just a few questions, 

Now installing this, do I need to uninstall the current drivers and how?  

seondly, After reading this.... if I undestand this right, I need t goto broadcoms website to download these drivers?

much thanks again!!

---

### Post by jan quark on 2008-02-08
first download everything you need

do not know if you have second internet connection :)

the native drivers can be disabled via the restricted driver manager
system > administration > restricted drivers managers


but one question:

if it ain't broken , do not fix it

it is my golden rule

broadcom cards can be very problematic or just work with ndiswrapper
when everything is fine I would stay with the working native drivers

pls post the output of

```
iwconfig
```

---

### Post by whos2know on 2008-02-08
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"PostCereals"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:18:39:6B:5E:6A   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=40/100  Signal level=-73 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:2463  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I have to agree but this is getting crazy... I really don't like how slow it is!!  and it also disconnects and reconnects a lot....

thank you again!!

---

