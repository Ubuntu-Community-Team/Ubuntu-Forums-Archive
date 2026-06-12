---
title: "Wireless PCMCIA card on Toshiba laptop"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by cune on 2007-09-02
Hey there,

I'm a new Ubuntu user, just switched. I have a Toshiba laptop with an onboard wireless chipset, but I want to use my PCMCIA card for its antenna.

The card is a Senao card, using the Prism 2.5 chipset (which should be supported I think).

Ubuntu sees the card, its listed as "INTERSIL HFA384x/IEEE" in the wireless connection dropdown, and it seems to find my network.

However, it won't connect to it at all. It tries to connect, but just gets stuck. The icon for the wireless connections program is showing two grey spheres and playing its animation. It also seems to lock out the rest of the system when it does this.

I know that my network is fine when I use my onboard chipset, and that it uses DHCP.

What can I try to fix this?

---

### Post by shearn89 on 2007-09-04
Open a terminal (applications -> accesories -> terminal) and type "lspci" and "iwconfig" with the card plugged in, and post the output here. We'll see what we can do!

---

### Post by cune on 2007-09-07
Here is the result of iwconfig:

```

lo        no wireless extensions.

wifi0     no wireless extensions.

Warning: Driver for device ath0 has been compiled with version 22
of Wireless Extension, while this program supports up to version 20.
Some things may be broken...

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi1     IEEE 802.11b  ESSID:"freenetanessen&#65533;"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:B9:CE:3F   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:"freenetanessen&#65533;"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:5B:B9:CE:3F   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-33 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

and here is lspci output:

```

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

```

Still nothing working so far, the card works great on my windows install however.

Is this likely to be some strange proprietary Toshiba hardware problem, maybe with the card reader?

---

### Post by cune on 2007-09-08
I did manage to get the card to work with Kismet, so maybe its not a hardware fault?

---

### Post by shearn89 on 2007-09-08
If it works with Kismet it won't be a hardware problem - Wifi is often tricky to set up in Linux. I can't see off the top of my head what could be causing the problem, except for the fact that there are 3 cards listed that have wireless extensions. You could try editing the /etc/network/interfaces file (i think its called that), and commenting out some of them. Failing that i can recommend having a look [here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-87da1b42f569991f8579034710220c47504eccaa") - it helped me get mine sorted.

---

### Post by cune on 2007-09-08
OK, interesting thing, I was following the guide you posted and I typed in:

```
sudo dhclient wlan0
```

and it worked! But,

```
sudo dhclient wifi1
```

Give errors about the hardware address, the same ones that I get when I run "ifup -a" and it fails.

So, dhclient wlan0 works fine, it gets an IP address from the router and it works, but of course the network manager does not update to reflect this.
dhclient wifi1 tries to get an IP and fails.

Looks like the OS is trying to use wifi1 instead of wlan0 in NetworkManager. How can I stop it doing this and get an IP automatically when I select my network?

---

### Post by shearn89 on 2007-09-11
> **cune said:**
> 
Looks like the OS is trying to use wifi1 instead of wlan0 in NetworkManager. How can I stop it doing this and get an IP automatically when I select my network?

This could possibly be sorted by removing wifi1 from the /etc/network/interfaces file. Back it up first, then comment out those lines, and see if that helps.

---

### Post by stchman on 2007-09-11
That Atheros 5005EG should work out of the box.  Are you using Feisty?  If so the restricted driver should be enabled by default.  If you are using something older than Feisty then you may need the madwifi drivers.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

---

