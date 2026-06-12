---
title: "Atheros AR5005G"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by linuxguy123 on 2006-12-28
Hello! I am a new ubuntu user (just emigrated from Fedora 6). I have an Acer Aspire laptop with an Atheros AR5005G 802.11abg NIC. With Automatix, I installed ndiswrapper. I am not sue if I have the wireless card installed. I added the network applet to my panel and the only connections it shows me are eth0 (my wired internet that im using now) and lo, which doesn't work for me. I would like instructions on installed/setting up my wireless internet connection. Remember, I am a complete newbie to ubuntu and not that familiar with sudo/apt-get, though I am familiar with yum, which, to my understanding, is similar to apt-get.

here is my info when i enter lspci and and iwconfig

------------lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
ronnie@ronnie-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:53794  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ronnie@ronnie-laptop:~$ iwlist ath0 scanning
ath0      Scan completed :
          Cell 01 - Address: 00:16:B6:40:83:68
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/94  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:18:4D:53:7B:F0
                    ESSID:"GeekSquad"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f0101001dff7f

ronnie@ronnie-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

---

### Post by linuxguy123 on 2006-12-28
------------iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:62618  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by linuxguy123 on 2006-12-28
UPDATE

I just installed Network Manager and it shows me two wireless networks (linksys and GeekSquad). I am assuming it CAN detect my wireless card. But now I have another issue...

When I try to connect to linksys, it asks me for a passphrase, and there is a textbox next to it.. There is also a drop down menu above that with "WEP 128-bit Passphrase" selected. Below the passphrase text box is a drop down menu selected as "Open System." I do NOT know what the passphrase is, nor what I should enter. I only have a wireless laptop, not a desktop PC. Do I need to have a desktop PC connected with wired internet to allow my laptop to use wireless internet? Thanks.

---

### Post by thankyousam on 2006-12-28
just go get things straight, you have the atho1 interface working? and when you click on the wireless monitor applet it shows a connect active and under support you get an IP address? And when you click configure your settings are set to DHCP? 

Remeber: If the wireless network you are connecting to has a WEP key it will probably be in Hex. Is' linksys' your router?

---

### Post by thankyousam on 2006-12-28
Typically, I've had to input the wireless network's name but you say they are being read and shown. That makes me curious to know what version of Ubuntu you're running?

---

### Post by linuxguy123 on 2006-12-28
> **thankyousam said:**
> just go get things straight, you have the atho1 interface working? and when you click on the wireless monitor applet it shows a connect active and under support you get an IP address? And when you click configure your settings are set to DHCP? 

Remeber: If the wireless network you are connecting to has a WEP key it will probably be in Hex. Is' linksys' your router?

My answer is that I assume so for the first question. The only thing I have is this laptop and my cable modem. I do not have a router. I am also unaware of my WEP key or how to acquire one. I need help on that. My laptop is automatically detecting two networks in my area; linksys and GeekSquad. This was the case on my Windows XP partition as well.

So basicly, I assume ubuntu is reading my wireless hardware. My problem is now acquiring a "passphrase" that the linksys network asks for when I try to connect. Do i need to have a desktop computer connected to the internet to enable my laptop to use wireless internet?

Here's a screenshot of what I'm talking about

[[IMG]http://img152.imageshack.us/img152/6831/screenshotgt4.th.png[/IMG]](http://img152.imageshack.us/my.php?image=screenshotgt4.png)

I am also using ubunutu 6.10 Edgy, the latest version I believe.

---

### Post by thankyousam on 2006-12-29
It sounds like your wireless card is working correctly, like you assumed because of the wireless networks it detected. However, if 'linksys' is not your router and it is WEP protected you will have to ask the administrator of the router for the WEP key. There are some programs that can break the encryption and produce a WEP key that will work but I will not go any further down that avenue. 

If what you have is a laptop and a cable modem, I assume from Cox cable or Comcast, you need a wireless router. It's fairly simple: Connect the Internet source to a wireless rounter you buy (linksys, netgear, etc.) via an ethernet cord. You will have the ethernet cable running from the cable modem to the router and if you have a desktop another ethernet cable will be running from the router to it. Something like this:[IMG]http://ramsites.net/~byerssw/basicwireless[/IMG]

If I'm reaching into the wrong direction with this explanation and you already know this and your question is more complex than please explain it in different words. 

On the side: does the linksys network work with windows? Or does it also require a WEP key?

---

### Post by linuxguy123 on 2006-12-29
On Windows, the same thing happens to me; a passphrase (or WEP key) is required and such. For now, all I have is a laptop and the cable modem; however, I have a desktop pc that im going to set up right now. If I connect the cable modem directly to my desktop pc with the ethernet cable, do I still need the wireless router for my laptop? i could swear that I have seen it done without a wireless router. if my words are confusing please let me know. Thanks!

---

### Post by thankyousam on 2006-12-29
If your desktop runs Windows you can enable connection sharing and use a wireless adapter of some kind (PCI, USB, ETC.) to share the connection amongst other computers. This carries disadvantages: if the sharing computer shuts down all computers receiving the connection lose it and the Desktop would always have to be connected. Doing this in Windows is easy: go to network connections and right-click for properties, go to wireless networks tab and add and network. This is were you will put all of your network specifics. You input the name and WEP key you want, the network should be 'Open', remember to check the ad-hoc network box so it doesn't try to use access points and click ok! If you have an internet source feeding into the desktop and a wireless adpater than the ad hoc network will share the network with your wireless laptop. 

For Ubuntu: To be able to use the ad hoc network you have to enable it, go to the terminal and type: sudo iwconfig ath0 mode Ad-Hoc

type: iwconfig to check and see if Ad-Hoc was enabled. 

If desktop is Ubuntu:
There has been some problems with creating ad hoc networks through ubuntu because of obvious wireless NIC support issues that all distros have. I recommend an Atheros wireless NIC for your desktop as well. 
Configure the wireless adpater to whatever IP address you want (192.168.0.1,netmask:255.255.255.0, gateway: nothing) And 
type, 
sudo iwconfig ath0 mode ad-hoc 
Your Ubuntu Desktop should be broadcasting. Just set your laptop to 192.168.0.2 and the gateway to 192.168.0.1

Even with these instructions the Ubuntu ad-hoc creation might not work. 
If these instructions don't cover something it's because I've never done this, it's fairly easy in theory but I've never had the reason to make an ad hoc network. Hope it helps anyway.

---

