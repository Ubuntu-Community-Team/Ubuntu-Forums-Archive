---
title: "Wireless Network Connection Problem"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by p4rk3r on 2007-08-20
I am having problems connecting to my wireless router.  My router is a D-Link which is Linux compatible (I base this off of the penguin logo and its instruction to find the user manual with Linux).  My wireless card is a HWPG1 hawking technologies. I think the wireless card is the problem.  I went to their website for tech support [http://www.hawkingtech.com/support/details.php?CatID=19&FamID=33&ProdID=290](http://www.hawkingtech.com/support/details.php?CatID=19&FamID=33&ProdID=290) and it shows that there are no available drivers for Linux, but I am able to connect and get signal from my router, it just will not connect to the internet.  Is there nothing I can do?

---

### Post by rharriso on 2007-08-20
I had a similar problem with my Belkin card. My problem was fixed by manually setting to my specific wireless network. 

I assume your gui looks much like mine. Left click on the network icon in the top right. click on manual configuration. Deselect roaming mode, and enter in your networks information. Don't know why, but that worked for me.

---

### Post by p4rk3r on 2007-08-20
when you say enter your network information do you mean select the router im trying to connect to or actually enter in its ip and other information?

---

### Post by Gone fishing on 2007-08-20
I think first see if your wireless card has been recognized if you open a terminal and type iwconfig do you see the card? 

If so the net work GUI tool should configure it, however, I have never got this to work on automatic but always got it to work on manual after adding the  ESSID and the WEP key.

---

### Post by p4rk3r on 2007-08-20
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"Airport"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:24:5C:81:9D   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=48/100  Signal level:-75 dBm  Noise level:-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thats what im getting

---

### Post by Gone fishing on 2007-08-20
Ok if you use the Manual GUI settings can you ping the router? maybe you need also to disable wired lan card. Looks like it should work :)

---

### Post by p4rk3r on 2007-08-20
how can i use the gui to ping the router?

---

### Post by Kynan on 2007-08-20
you can go if using gnome to system > administration > network tools > ping tab
then simply type the ip there for gui.
I find it easier to just open up a terminal and type ping 192.168.0.1 for example.

---

### Post by Gone fishing on 2007-08-20
Sorry I was unclear what I meant was use the GUI tools to set the ESSID WEP password etc, then try and ping the router using a terminal

---

### Post by bigboy_pdb on 2007-08-20
You said that you appear to be connected to the router, but you cannot connect to the internet. Are there other computers on your router that are connected to the internet? Also, what encryption are you using?

---

### Post by p4rk3r on 2007-08-21
ok i have not tried pinging yet but i can get linux to connect to the router fine, it shows signal, says its connected, but when i try and access anything internet related it will not connect. im sure it isnt a router problem because i am currently connected by ethernet cable from that same router.

---

### Post by bigboy_pdb on 2007-08-21
I've tried looking for information on your card's chipset, but I couldn't find any. The following website has a list of manufacturers and cards and Hawking Technologies is on the list:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

You might want to contact them about your card because they might know something about it (and even if they don't it might help them to update their list). 

In order to find out if your card is compatible we need to find the chipset for your card.

Open a terminal (Applications -> Accessories -> Terminal) and in it type "lsusb". Post your "Ethernet controllers" and "Network controllers" here (and anything else that you're uncertain about). To give you an example of what it should look like, my wireless PCI card was:
02:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

With respect to your router being supported by Linux, the compatibility between the router and Linux shouldn't have anything to do with you being able to connect to the router via a wireless connection.

---

### Post by bigboy_pdb on 2007-08-21
I forgot to mention a few other things.

While doing the following you should set your router to "Broadcast" its signal. You should first try to connect to the router without encryption, meaning you should initially disable wireless encryption. Then, once you've gotten it working without any encryption, you should try using WEP. Then, once you've gotten it working with WEP encryption, you should try using other types of encryption (such as WPA or WPA2). The reason why you want to start off without encryption and then using WEP is because there are protocols for communicating with the wireless cards using these encryption settings and both should be well supported. Most cards have their own private interfaces that can be used to communicate with the card for other forms of encryption, but it may be a little more difficult to get your card working with these interfaces. In the future it should be easier, but I've found that there are some problems with trying to use the "Network Manager" to connect to wireless connections (when they use a form of encryption that is not WEP encryption).

Granted that you have a wireless network interface called "ra1", I'm thinking that your problem might be related to your encryption settings (in your router). It appears that you have a RaLink chipset in your card (which is the same type of chipset that I have) so if you get your card working without encryption and then with WEP encryption, I can probably help you to get it working with WPA encryption.

---

### Post by p4rk3r on 2007-08-21
I'm not exactly sure on what you mean by encryption.  I'm assuming you mean the WEP passwords and such.  And if that is the case I'm not using any and dont plan on setting up one.  Here is my lsusb:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

doesnt look to good :(

---

### Post by Gone fishing on 2007-08-21
I think you are probably connected to the wireless router now you need to set the IP address on the card and try to ping your routers IP address. 

i.e. if your routers IP address is 192.168.1.1 give the card 192.168.1.2 your routers handbook should tell you what IP address it uses

---

### Post by bigboy_pdb on 2007-08-21
Sorry about that. I meant "lspci" not "lsusb". Please try that again with "lspci".

**[EDIT]**
Another thing to check is that your router is using DHCP and not static IP addresses.
**[/EDIT]**

---

### Post by p4rk3r on 2007-08-21
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:09.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
00:09.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

What I'm guessing is that this problem has mainly to do with my wireless card and not the router.  The Hawking technologies website says there are no drivers supported for linux and it does connect to the router and get signal.  Also, my router's ip is set to 192.168.0.1 and when i attempt to ping it im getting "network is unreachable" and this is while the gui is showing connection and signal to the router.

---

### Post by p4rk3r on 2007-08-21
the router is also using dhcp as well. sorry i forgot to say that lol

---

### Post by bigboy_pdb on 2007-08-21
The following line indicates which chipset your wireless card is using:
00:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI

The chipset is what matters when you're trying to solve wireless networking problems and yours is a RaLink RT2561/RT61 chipset. You might want to try doing searches using "RT2561" or "RT61" as search terms and see what comes up. I would do this myself to help you but I have to go out. When I get back, I'll try to offer more help (but there will still be other people helping in the mean time).

From what was listed by your iwconfig it appears that your drivers/modules are functional. It would be a good idea to see if you can ping the router (as some other people had suggested) to see if you are connected to it. Your router's IP address is the one that you would have used to change/check its settings beforehand. If you can ping the router, try pinging a website such as google.com. If you find that you can ping the router but not a website, try releasing and renewing the router's IP address and then try again.

---

### Post by p4rk3r on 2007-08-22
havent been able to find anything to fix the problem yet with the searches. And when I disable my wired connection to my router I am unable to ping it, even though my gui is showing I'm connected and have signal from the router.

---

### Post by bigboy_pdb on 2007-08-25
Apparently some people have problems getting their wireless connection to work with the default Ubuntu modules for some RaLink chipsets (I don't know if this applies to your chipset or not). It might be a good idea to try to compile a new module, load it, and see if it works.

You could try compiling the serialmonkey drivers, which can be found on this page:
[http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads)

There's also a driver for your card on RaLink's website. I think that they might have copies of the serialmonkey drivers though. The link is:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
(The link for it is in the second row of the table)

If you decide to try to compile the module, you should first install the "build-essential" package. To do this open "Synaptic Package Manager" (System -> Administration -> Synaptic Package Manager), search for "build-essential", click the box beside it and click "mark for installation", and then click the "Apply" button.

The instructions for building the module and inserting it into the kernel (regardless of which version you use) is in the README file. I don't think that there's a step (in the README file) for removing the original module from the kernel so you might want to use "rmmod" to do that first (you can use "lsmod" to see what modules have been inserted into the kernel). For more information on the command "rmmod" you can view the man page for it by typing "man rmmod" in a terminal.

---

