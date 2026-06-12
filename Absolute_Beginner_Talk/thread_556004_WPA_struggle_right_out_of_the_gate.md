---
title: "WPA struggle right out of the gate"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by CamChain on 2007-09-20
New to Ubuntu and already struggling with trying to get my new laptop connected to my wireless network. I bought a Dell 1420 preloaded with Feisty Fawn and tried to get connected to my home WPA2 network. The network settings sees my network and others around me, but only offers up WEP. I browsed the forum and tried installing wpa_supplicant. Still only see WEP. 

Being new to Ubuntu/Linux everything is a bit foreign to me. It never even occurred to me that standard wi-fi security schemes would be foreign to Ubuntu. 

Am I missing something obvious? :( How do use my WPA2 connection? :confused:

---

### Post by mikewhatever on 2007-09-20
What wireless card is there? In my case, it is XP that has no support for wpa2, so I use wpa, but both options are present in Ubuntu. To check your wireless card type > sudo lshw -C network

Here is mine >  description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation


---

### Post by CamChain on 2007-09-20
> **mikewhatever said:**
> What wireless card is there? In my case, it is XP that has no support for wpa2, so I use wpa, but both options are present in Ubuntu. To check your wireless card type 

Here is mine

Intel PRO/Wireless 3945ABG.  A quick check online indicates it supports WPA2.

BTW - Thanks for the command to get this info :)

---

### Post by NCFC on 2007-09-20
Can I assume that you using Gnome Network Manager?  If so, get rid of it and go for Wicd.  I had nothing but problems with Network Manager (WEP only), but Wicd and wpasupplicant worked great right from the very beginning.

MOBO Asus M2N32-SLI Deluxe Wifi-AP Solo
Linksys WRT54GL router with tomato 1.07 firmware.

---

### Post by Chris S. on 2007-09-20
> **CamChain said:**
>  I browsed the forum and tried installing wpa_supplicant. Still only see WEP.

With wpa_supplicant, unless you are using a GUI front-end, you won't "see" anything.  You need to configure and run wpa_supplicant separately from any other wireless managers (which should probably be shut down for best results).

Try "man wpa_supplicant" for some direction on how to set it up and use it.  There are some example configuration files in the man pages, which you can access directly at /usr/share/doc/wpasupplicant/.

---

### Post by CamChain on 2007-09-20
> **NCFC said:**
> Can I assume that you using Gnome Network Manager?  If so, get rid of it and go for Wicd.  I had nothing but problems with Network Manager (WEP only), but Wicd and wpasupplicant worked great right from the very beginning.

MOBO Asus M2N32-SLI Deluxe Wifi-AP Solo
Linksys WRT54GL router with tomato 1.07 firmware.

Yes, I'm using Gnome Network Manager, which only shows WEP. Will it cause any kind of conflict having both installed? And will I need to do some manual entries for wpa_supplicant config file (wherever that is)?

---

### Post by CamChain on 2007-09-21
I ran **iwlist **scan and the info all looks good to me. Got info on three other neighboring networks also. None have WPA available in the* Network Manager* setup. 

Is *Network Manage*r capable of showing a dropdown for WPA 1/2?



eth1      Scan completed :
          Cell 01 - Address: 00:16:B7:AB:A3: DE
                    ESSID:"Coyote"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6 
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s 
                    Quality=98/100  Signal level=-26 dBm  Noise level=-26 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 180ms ago

---

### Post by NCFC on 2007-09-21
> **CamChain said:**
> Yes, I'm using Gnome Network Manager, which only shows WEP. Will it cause any kind of conflict having both installed? And will I need to do some manual entries for wpa_supplicant config file (wherever that is)?

Yes, you can only have one network manager loaded. 

If you download Wicd, then Network Manager will be removed.  Once you open the Wicd preferences, you will get to choose which wpa supplicant driver you require (wext for me).  I then opened the network, adjusted the encryption setting to WPA 1/2 and entered my network passphrase.  Took about 20 seconds and everything connected fine.

---

### Post by Travisher on 2007-09-21
Having messed around for hours, nay days, before reading the thread above - doing nasty things like iwconfig eth1 essid blah and dhclient eth1 and getting only the occasional connection and deciding nothing appeared repeatable.... I  can say that [http://wicd.longren.org](http://wicd.longren.org) and their Wicd tool really does work. Read the clear instructions on their website and go for it.
This  makes Ubuntu from an also-ran into the clear favorite for me to support a non techie sister-in-law's computing efforts.

---

### Post by CamChain on 2007-09-21
Thanks for the input. I think I'll sit on this for a few days, since I'm a bit nervous about screwing up and not having a connection to set it straight again. I really don't have a handle on the Linux OS yet. Like where are those config files and when and how do they get called.

I bought a couple of books about Ubuntu, but neither delve into Linux to any extent. I need to get a basic Linux book to get a feel for OS. Boot sequence, file system structure, executables, config settings, etc.

One of those books suggest to just over it, in relation to WPA. :-k  Just switch your network back to WEP and live it until an Ubuntu release supports it. 

Thanks again O:)

---

### Post by Paul_world10 on 2007-09-21
you could try modifing your      :    sudo nano  /etc/network/interfaces       :  file  thats in Dapper Drake though. Very Possible.

---

### Post by Buffalo Soldier on 2007-09-21
I have the same notebook and network card. I can confirm that Intel PRO/Wireless 3945 + Network Manager works out-of-the-box with WPA. But since I don't have a WPA2, I can not confirm on that.

I'm on Gutsy right now, nevertheless in Feisty you should see something the same like this. Just make sure you choose WPA2 on the drop down menu.

BUT, seeing that you've done some manual tweaking and changes to your config files... there are somethings that you need to do now.

Network-Manager is not going to handle any network interface that you have manually configured, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let Network Manager handle them.

```
sudo gedit /etc/network/interfaces
```

Example:> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp

---

### Post by bendystraw on 2007-09-21
WPA is very hard to set up, it took me about a week to get it setup, but i just installed a card i had laying around the house that was preloaded into ubuntu so i was ok,

A big hint, use NdisWrapper and/or MadWifi

---

### Post by NCFC on 2007-09-21
> **CamChain said:**
> Thanks for the input. I think I'll sit on this for a few days, since I'm a bit nervous about screwing up and not having a connection to set it straight again. I really don't have a handle on the Linux OS yet. Like where are those config files and when and how do they get called.

I bought a couple of books about Ubuntu, but neither delve into Linux to any extent. I need to get a basic Linux book to get a feel for OS. Boot sequence, file system structure, executables, config settings, etc.

One of those books suggest to just over it, in relation to WPA. :-k  Just switch your network back to WEP and live it until an Ubuntu release supports it. 

Thanks again O:)

While I feel your pain, because I too am new to Linux, I have found that using **Synaptic** and **Add/Remove** are very valuable tools rather than using Terminal at this point.  They have allowed me the opportunity to fine tune my install to something that I am pretty happy about right now.  Some tinkering is still required but I have everything running quite well, minus my webcam and NAS drive, but they are next.

My advise is to read, read, read and avoid using Terminal unless absolutely necessary.  My Wicd knowledge came from many forums (to find out what people were using) and the home site (to get the technical information).  Synaptic allowed me to download the packages that I needed and the setup was pretty easy after that.  

Please let us know how things turn out.

Cheers

---

### Post by CamChain on 2007-10-05
Thanks for the advice. I simply switched my home network to WEP and will live with that until a future release uses WPA natively. There is just far too much I have to learn, without making a crusade of beating my laptop into using WPA. The 50+ page thread on this forum helped with that decision :confused:. If something garners that many pages, there must be a lot to it :-k

---

