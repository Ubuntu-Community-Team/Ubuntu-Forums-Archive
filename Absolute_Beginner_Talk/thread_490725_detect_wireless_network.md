---
title: "detect wireless network"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by asic_fd on 2007-07-02
can ubuntu do automatic wireless search? just like in windows, all available wireless network are detected and you just choose one you want to use. 

Thanks.

---

### Post by wjp.reg on 2007-07-02
Check out this link for your answer:

[https://wiki.ubuntu.com/7.04Tour]("https://wiki.ubuntu.com/7.04Tour")

---

### Post by lousy.ratbag on 2007-07-08
> **wjp.reg said:**
> Check out this link for your answer:

[https://wiki.ubuntu.com/7.04Tour]("https://wiki.ubuntu.com/7.04Tour")how do i see/invoke the window shown at this link?  the function looks like what i want; but how do i get it?

---

### Post by Jareth on 2007-07-08
Just left click on the network icon at the top of screen, methinks.

---

### Post by lousy.ratbag on 2007-07-08
> **Jareth said:**
> Just left click on the network icon at the top of screen, methinks.tried that.  it offers "Wired Network" (greyed out), and "Manual Configuration" - the latter doesn't show anything like what that window included.  yes, i'm using wireless at the moment - each time i take my laptop to another place with another wireless network i have to manually select it & enter its WEP password

---

### Post by yungwunn911 on 2007-07-24
any updates on this? having the same issue!

-mike

---

### Post by anewguy on 2007-07-24
It would indicate that the system isn't seeing any wireless networks, and this is probably because of the driver for your wireless card.  Have you been able to connect wirelessly with Ubuntu before, or is this your first time?

There are many, many types of wireless cards out there and an equal amount of the hassles people have gone through in Linux to get it working.  If yours didn't work "out of the box" with Ubuntu, you will probably need to use ndiswrapper to install Windows versions of the wireless drivers in Ubuntu.  Once you have set everything up correctly, you will see any available wireless networks, and you'll be able to select which you want to connect to.

I created a simple how-to for my cheap laptop here:  [http://ubuntuforums.org/showthread.php?t=507505]("http://ubuntuforums.org/showthread.php?t=507505")

You may want to check that just to get an idea what can be involved, then come back to this forum and do a search on wireless and your wireless card - there will probably be hundreds of posts to look through for advice - maybe even a how-to!:)

---

### Post by yungwunn911 on 2007-07-24
my laptop is fairly new and has built in wireless....It may still not be supported?

I have a compaq v2000 (not sure what the card is..i guess ill have to try to find out..)

-mike

---

### Post by anewguy on 2007-07-24
BTW - forgot to mention that if you have wireless working, you may want to reinstall network manager or install network-manager-gnome.

To remove your current network-manager:

- get into a terminal and type:

    sudo apt-get remove network-manager

after that completes:

   sudo apt-get install network-manager network-manager-gnome

after that installs, I can't remember if you have restart or not to see the changes.  Either way, check under you network icon on the top bar now and you should see wireless networks.

Also - If you are having to enter WEP passwords everytime you go to a network, you need to check on getting the keyring manager working.  Currently I'm in Windows, so I don't remember what you have to do synaptic package manager to get it and install it.:)

Hope some of this helps in some way!:)

---

### Post by anewguy on 2007-07-24
> **yungwunn911 said:**
> my laptop is fairly new and has built in wireless....It may still not be supported?

I have a compaq v2000 (not sure what the card is..i guess ill have to try to find out..)

-mike


It is more likely than not that it is NOT supported directly out of the box.  Go into a terminal window and type:

   lspci

then post the results back here and we can give you a better idea.

---

### Post by yungwunn911 on 2007-07-24
my results. 

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
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
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


ps im hooked up to the internet via wired LAN

-mike

---

### Post by kevdog on 2007-07-24
This is your wireless card

> 05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

It does not work out of the box with Ubuntu.  You will either need to install the drivers via bcm43xx or ndiswrapper (which requires a copy of the Windows Xp drivers).

---

### Post by anewguy on 2007-07-24
Sorry I didn't catch this right away but I've been away from my PC resting my eyes!  Anyway, your wireless card is the same as mine, so I suggest you follow my instructions posted back on the first page to go to my laptop instructions and just follow the part about getting the wireless working - it should work fine for you as well!:)

Good luck, and please post back after you've followed my instructions and let us know how things went.:)

---

### Post by yungwunn911 on 2007-07-24
> **anewguy said:**
> Sorry I didn't catch this right away but I've been away from my PC resting my eyes!  Anyway, your wireless card is the same as mine, so I suggest you follow my instructions posted back on the first page to go to my laptop instructions and just follow the part about getting the wireless working - it should work fine for you as well!:)

Good luck, and please post back after you've followed my instructions and let us know how things went.:)

thanks, i found a blog online that allowed me to download a packet which automatically installed the wireless for me! works like a charm!

thanks, 

mike

---

### Post by Crafty Kisses on 2007-07-24
> **asic_fd said:**
> can ubuntu do automatic wireless search? just like in windows, all available wireless network are detected and you just choose one you want to use. 

Thanks.

Yes, most wireless cards can be detected, but if not, you can always use a NDISWrapper, and install the proper drivers that way, hope this helps.

---

### Post by anewguy on 2007-07-24
Glad you got it working!  For you new users out there reading this - you may run into this also, but it normally isn't very difficult to get things working, so go ahead and try Ubuntu!:)

---

### Post by yungwunn911 on 2007-07-24
> **anewguy said:**
> Glad you got it working!  For you new users out there reading this - you may run into this also, but it normally isn't very difficult to get things working, so go ahead and try Ubuntu!:)

yes your right. I have to admit that it runs VERY fast on my laptop. 

for anyone that has a V2000 series Compaq laptop refer to this blog page for installation

[http://joshuadavis.wordpress.com/2007/04/12/fully-working-ubuntu-with-a-compaq-presario-v2000/#comment-424](http://joshuadavis.wordpress.com/2007/04/12/fully-working-ubuntu-with-a-compaq-presario-v2000/#comment-424)

-mike

---

### Post by gdupont on 2007-09-17
I got ubuntu on my dell laptop and recently try to make the wireless card work but without any success. The driver are loaded through ndiswrapper and here is the lspci line about my card : 

0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

Well I see it on a iwconfig :

eth0      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I just reinstall the network-manager as you advised but nothing more... the wireless network button is not accessible.

Looking for more advices...

---

