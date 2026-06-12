---
title: "[SOLVED] Really need wireless help... :("
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by dorkdork777 on 2007-01-24
First of all, I'm a complete noob to most of this Linux stuff, the only things I really know how to do are to run apps, and look into folders. That's about it. I'm good with Windows, but this whole Ubuntu stuff is like a whole new confusing universe...

I can my wireless internet from Windows and a Mac fine, same goes for my PSP and Wii, but Ubuntu Dapper picks up every network around me except the one I want to connect to, and Edgy fails to find any at all... :(  (I tried connecting to another network, it doesn't work.)

I heard that lspci might help, so here's my results - 

```

lspci results (edgy)

00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1)

lspci results (dapper)
0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:01:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:06:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 TurboCache(TM) (rev a1)

```

I hope that helped. I'm posting from Windows, so I need to restart once I'm in Ubuntu (installed 6.06 Dapper) to download stuff or read more suggestions. Also, my wireless card is Netgear WG311 v1.


I tried ```
sudo iwconfig ESSID parkynet channel 13
``` It gives me ```
Error : unrecognised wireless request "parkynet"
```

This:```
uname -r
``` gives me ```
2.6.15-26-386
```

I found [this]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") webpage, which has details of all fo the working cards for NdisWrapper. My card wan't there, but I found another card with exactly the same chipset as mine - 

```

Card: Netgear WG511T 108Mbps Cardbus adapter (with super G)

    * Chipset: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
    * pciid: 168c:0013
    * Driver: Windows XP driver available on the Netgear CD: netw511.inf + wg511nd5.sys Native
    * Driver: MadWiFi[216]
    * Other:Tested with ndiswrapper 1.2 source compile Note: It's needded 2.6.11.7 kernel with no ACPI support (otherwise kernel risks to crash) 

```

Would it hurt to give me a simplification of these instructions, so I could try it out? Or would it just not work? Or could someone give me a few hints? This is so confusing... :( I've been looking to make the switch to Ubuntu for around six months, but I couldn't as wireless doesn't work.

BTW, I posted this in the Network and Wireless section, but I didn't get many replies at all, so I'm posting it here.

EDIT, 26/11/2007 - The problem turned out to be a faulty router, nothing to do with Ubuntu. All is working fine now, and thread marked as solved. :)

---

### Post by lyceum on 2007-01-24
I am not an expert, but I can say that I had the same problem, I ended up typing in my router and hex password and it worked. I am guessing you tried that already though?

---

### Post by annda on 2007-01-24
some cards have problems with WEP encryption - do you have it enabled? can you temporarily switch it off to see if you can connect without it?

also, i know it's pretty long but very useful resource:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

first check out the parts with iwlist and Config files.

a little shortcut:
i assume your wireless device is ath0 (test with iwconfig command) - what happens when you type this:

```

sudo iwlist ath0 scan
```

---

### Post by dorkdork777 on 2007-01-25
I've got no encryption whatsoever. And I'll try that command, thanks for all the help! :)

---

### Post by dorkdork777 on 2007-01-25
OK, I've done the command. It gave me this - 

```
ath0      Scan completed :
          Cell 01 - Address: 00:0D:72:33:AC:99
                    ESSID:" "
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:11:50:E1:A1:88
                    ESSID:"Belkin_G_Plus_MIMO_ADSL"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:11:50:E1:A1:88
                    ESSID:"Belkin_G_Plus_MIMO_ADSL"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/94  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:0F:B5:CE:D2:0A
                    ESSID:"piano"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=8/94  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f20 2

```

My network isn't there. :(

---

### Post by Stochastic on 2007-01-27
I've got that same chipset (Atheros AR5212 802.11abg NIC (rev 01)) in a D-Link DWL-G650 and Dapper works great for me but Edgy is not so forgiving (supposedly it's fixable).  I'd recommend attempting to connect to another router/location and then going back to your own.  I've had it happen once or twice where the card doesn't see my own network but that usually fixes it for me.

The fact that you're able to see details of other networks suggests that the card is configured correctly.  I'd open System>Administration>Networking rather than doing this via terminal if you can.  That has always worked for me.

---

### Post by dorkdork777 on 2007-01-27
OK, I'll give that another try. Thanks for the reply. :)

---

### Post by dorkdork777 on 2007-01-27
Didn't work. Does it matter that the router is a NETGEAR DG843G?

---

### Post by VorDesigns on 2007-01-27
These are the steps I took to get my D-Link DWL-G650 card running:  There are probably much betters ways but this worked for me after two weeks of trying, reinstalling, buying a different card, trying KUbuntu, reinstalling Dapper 6.06 LTS.

sudo gedit /etc/network/interfaces
## I commented out all eth_ interfaces, I'm never using this on a wired network.

auto ath0
iface ath0 inet dhcp
## Added as per other posts but the value of this is unknown
pre-up ifconfig ath0 up
pre-up ifconfig ath0 down
pre-up ifconfig ath0 up
## Added as per other posts
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
## Added by the Network applet but it doesn't work
wireless-key <my_secret_code_was_here_> // put yours in place
## Added as per other posts to identify the access point I want
wireless-ap 00:00:00:00:00:00  // put your AP MAC here.
## on the channel it uses
wireless-channel 9
## by the name I gave it
wireless-essid my_access_point_id
## in the manner it communicates
wireless-mode managed

I then rebooted and still couldn't connect so I spent time reading a lot of the MadWiFi help documents.

To get it running post boot everytime until I figure out how to get the following scripted and loaded post boot.

## This tells the secret code that should be loaded already
sudo iwconfig ath0 key <my_secret_code_was_here_> // put yours in place
## This tells the authentication mode 1 for open, 2 for Shared key
sudo iwpriv ath0 authmode 2
## Now that the ap and ath0 should be talking, ask for an IP
sudo dhclient ath0

At step two of the commands above, my card goes from cycling lights (zombie mode) to syncrhonous lights (connected mode).  Then, the last step asks for an IP again.

---

### Post by dorkdork777 on 2007-01-27
Thanks! But what should I do about enryption? I have no security on my network, so I don't know what to type.

---

### Post by VorDesigns on 2007-01-27
Can you connect to your AP at all?
Scrath that.
--
Read my post and set the items that you can on your AP.
I would pick another channel other than 6, try 3 or 9, you might try each to see if it shows up better on one over the other.  I found my area saturated with everyone (eight) ganged together on channel 12.
set the ESSID
set the channel
set the MAC address of the router

See if your card gets synch and then try the sudo dhcp client command

Otherwise, turn on encryption and set that up while you are at it.

I use WEP because TKIP didn't work no matter what I tried.

---

### Post by dannyboy79 on 2007-02-08
edgy and wg511t is not good out of the box supposedly per this link. [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)
madwifi fixed this issue around 2/6/07 for the wg511t, Gnome NetworkManager (using wpa_supplicant, using madwifi-ng, using ath_pci).

---

