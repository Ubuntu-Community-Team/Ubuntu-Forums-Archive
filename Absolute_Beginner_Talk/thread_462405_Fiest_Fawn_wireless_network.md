---
title: "Fiest Fawn wireless network"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by JupiterMike on 2007-06-02
I finally got Fiesty Fawn installed on my laptop, but I cannot get my wireless network card/connection to work.  I'm using a D-Link AirPlus G DWL-G630 card.  I won't list all the fixes I've attempted.  Sooo- can any tell me the correct procedure???

---

### Post by kernel tom on 2007-06-02
first step would be to make sure ur card is on

go to Network Settings... then see if there is a check mark in the box enabling your card, you may need to know ur exact network name to connect....

also, if you have another way of connecting to the interenet, ie wired, i suggest downloading wlassistant

sudo apt-get install wlassistant
then run
sudo wlassistant

it will configure and connect you wirelessly and save all of ur settings and keys

---

### Post by The Mekon on 2007-06-02
I have a D-Link DWL -630G using the RT61 chipset on my laptop and had a little trouble setting up at first until I did it manually.

First bring up a terminal and enter:

 iwconfig 

This should show a list of network connections and if your D-link has a RT61 chip set it should be identified at ra1 or one of the available network connections - in my case it is ra1.

Next ensure that you set your wireless connection settings to manual by selecting:

System/Administration /Network  (you will need to enter your user password)
 
Click on the Wireless connection and select properties.  Make sure the "Enable roaming mode" box is not ticked.  You can try and enter your network details Such as Essid, Password type and key and and your connection  configuration then click OK.

Now go back to the terminal again and enter:

sudo iwconfig 

and you should get something like this:

brian@brian-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra1       RT61 Wireless  ESSID:"ATHOME"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:28:63:B7   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:94AB-E6C5-D7
          Link Quality=69/100  Signal level:-62 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you can see your Essid, Encryption Key and get a good link quality you are in.

Unfortunately the network connections did not stick at first for me so I resorted to manual means.

Back in the terminal I entered the following.
 
sudo iwconfig ra1 Mode managed
sudo iwconfig ra1 key open 94:ab:e6:c5:d7
sudo iwconfig ra1 essid ATHOME 

Note that this sets a WEP key - I haven't made WAP work yet.
ATHOME is my wireless routers ESSID .

sudo iwconfig

should now show a nice connection.

After rebooting your wireless should be OK

Brian

---

### Post by JupiterMike on 2007-06-03
Brian;  Thanks for your advice.  I tried doing what you advised.  Now when I go to Network Settings it looks like my link is OK. Check Mark in small square, Black Tower with Red activity waves, ESSID shows, Address is DHCP,  but I still cannot get wirekess connection to internet.  Maybe the chipset in my card is incompatible with Linux.  I don't know how to get chipset number.  I've Emailed D-Link asking them for info.  Thanks again--Mike C.

---

### Post by The Mekon on 2007-06-03
Let us start again.

In a terminal type:  "lspci"

I get:

brian@brian-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1420
02:06.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
03:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
brian@brian-laptop:~$ 

Which right at the bottom shows me that I have a Network Controller RaLink   etc.

This is the D-Link card I am assuming that you have got.

If so you should be able to set it up manually but you have to make sure that the Network Manager is disabled.  I have actually used Synaptic Package Manager to delete it.

Now check what your wireless network uses for:

ESSID

Security WEP or WAP  (I can only get WEP to work)

Security key (normally 10 hex digits ie mine is 94abe6c5d7)



If you are using WEP then repeat the steps I recommended in my previous message.

Then in the terminal type:  "sudo ifup ra1

You should now have a connection.

I have just re-setup my wireless connection using this and if this gets posted it obviously works:p.

Brian


PS In the terminal type "gedit /etc/nertwork/interfaces.

This should show something like:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet dhcp
wireless-essid ATHOME
wireless-key 94abe6c5d7

auto ra0

auto eth0


iface ra1 inet dhcp
wireless-essid ATHOME
wireless-key 94abe6c5d7

auto ra1



The setting for ra1 shows that it has "stuck

---

### Post by JupiterMike on 2007-06-04
Brain;  Thank you, I hope I've not become a pest, but here goes again. I have been following your steps.
In terminal I typed "Ispci"
 
I got.

michael@ubuntu~$
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/838365 [KT133/KM133 AGP
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686{Apollo Super South} (Rev40)
00:07.1 IDE Interface: VIA Technologies, Inc. VT82C586A/B  VT823x/A/C  PIPC Bus Master IDE (Rev06)
00:07.2 USB Controller:  VIA Technologies, Inc.  VT82xxxxx UHCI  USB !.! Controller (Rev 1A)
00:07.3  USB Controller:  VIA Technologies, Inc. VTxxxxx UHCI USB 1.1 Controller (Rev 1A)
00:07.4  ISA bridge:  VIA Technologies, Inc. VT82C686 {Apollo Super ACP1] (Rev40
00:07.5  Multimedia Audio Controller:  VIA Technologies, Inc.  VT82C686 AC97 Audio Controller (Rev50)
00:07.6  Communication Controller:  VIA Technologies, Inc. AC97 Modem Controller (Rev30)
00:0a.0  CardBus bridge: Texas Instruments PCI1420
00:0a.1  CardBus bridge: Texas Instruments PCI1420
00:0e.0  Firewire (IEEE 1394)  Texas Instruments TSB12LV26 IEEE-1394 Controller (link)
00:10.0  Ethernet Controller: RealTek SemiConductor Co., LTD. RTL-8139/8139C+ (rev10)
01:00.0  VGA Compatable Controller: ATI Technologies, Inc. Rage Mobility P/M AGP 2X (Rev64)
06:00.0  Network Controller: Texas Instruments ACX 111 54Mbs Wireless Interface
michael@ubuntu:~$

My ESSID is USR5461
no encryption

Unless I've done something very wrong everything seems OK except I cannot connect to the internet.

By the way, D-Link answered my Email by saying the the information I requested was "Proprioritary Information which they would be glad to share if I wrote them on "Company Letterhead"  and after my request was approved.  Oh Well!!!:tongue:

---

### Post by The Mekon on 2007-06-04
The important line is:

06:00.0 Network Controller: Texas Instruments ACX 111 54Mbs Wireless Interface

Which is a totally different chip set to mine.

In a terminal type "iwconfig"

and check where the wireless connection is.  For example wlan0, eth0 ra0 etc.  It should show some thing like ACX 111

Now try again assuming it's wlan0.

sudu iwconfig wlan0 mode Managed
sudo iwconfig wlan0 key off
sudo iwconfig wlan0 essid  USR5461  (make sure the case is right!)

Then check with sudo iwconfig to see if these parameters are correct, reboot and try again.

If all else fails try a search for  ACX 111  to see how othe forum members have dealt with this.

Brian

---

### Post by JupiterMike on 2007-06-06
Brian;
  I must thank you again for all the hard work I've put you through.  I finally am able to connect to the internet.
There must be something strange with the AXC 111 chipset.  What I finally did waas to use my daughter's AT&T  Plung & Share card instead of the D-Link card.  Works fine with Ubuntu but not with XP.  The D-Link card works fine with XP but not with Ubuntu.  So I just keep both cards handy.  Thanks again.

---

