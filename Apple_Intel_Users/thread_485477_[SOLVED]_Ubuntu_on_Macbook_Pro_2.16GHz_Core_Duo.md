---
title: "[SOLVED] Ubuntu on Macbook Pro 2.16GHz Core Duo"
date: 2007-06-26
forum: Apple Intel Users
---

### Post by maluka on 2007-06-26
Hi
I'm trying to do an install of Ubuntu on my one year old MBP using Boot Camp.  I tried installing it straight off the 7.04 cd but i ran into trouble.

i am posting links to photos of the error:

[http://i16.tinypic.com/4r27rdk.jpg](http://i16.tinypic.com/4r27rdk.jpg)

[http://i16.tinypic.com/4u2cgok.jpg](http://i16.tinypic.com/4u2cgok.jpg)

could it be that i need to download a different ubuntu build?

when doing the install i followed these instructions as well:

"To prevent a kernel panic which might occasionally occur, press F6 and enter one of the following parameters at the boot: prompt:
lpj=8000000 (for 2 GHz MacBook)..."

since i have a 2.16GHz MPB, would i need to enter a different number perhaps?


i get taken back to ubuntu@ubuntu:-$_

could i enter something here to make it install?

---

### Post by ivesjd on 2007-06-26
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) That should get you going.
Thanks to ronocdh for use of his sig :P

---

### Post by maluka on 2007-06-26
thank you very much!!!:p

---

### Post by maluka on 2007-06-27
i've installed and am running!!!:popcorn::p

---

### Post by ivesjd on 2007-06-27
Congrats! :D

---

### Post by ronocdh on 2007-06-27
> **maluka said:**
> i've installed and am running!!!:popcorn::p
I'm glad ivesjd jumped on this so quickly. Just wanted to say "good form" by posting pics of the error! :D

---

### Post by maluka on 2007-06-27
thanks :p i figured the pics could probably explain it better than what i could. now it's on to getting wifi working....

---

### Post by NickFury on 2007-06-29
> **maluka said:**
> thanks :p i figured the pics could probably explain it better than what i could. now it's on to getting wifi working....

I have a have MacBook Pro C2D..

Macbook Pro C2D 2.16Ghz
2GB ram 
120gb hd
etc

If you have a regular Core Duo (note: not C2D) then wireless should already be working, if you have a C2D; then you NEED the MadWiFi Driver..  (well you may not need it; but i found it much easier then trying NDISwrapper or anything)


I grabbed the MadWifi 0.9.30.13 drivers.. here...
[http://snapshots.madwifi.org/madwifi-hal-0.9.30.13/](http://snapshots.madwifi.org/madwifi-hal-0.9.30.13/)
(I downloaded the May 19th snapshot)


Then did (assuming you are in the directory where you downloaded the MadWifi drivers too...)

```
tar -xvfz madwifi-hal-0.9.30.13-r2351-20070519.tar.gz	
```

```
 cd madwifi-hal-0.9.30.13-r2351-20070519 
```

```
make clean
```

```
sudo make
```

```
sudo make install
```

```
sudo modprobe ath_pci
```

Then I right clicked on the network applet in the upper right, and I saw wireless networks!  Easy as pie :D


Hope that helps!

---

### Post by cyberdork33 on 2007-06-29
> **NickFury said:**
> If you have a regular Core Duo (note: not C2D) then wireless should already be working, if you have a C2D; then you NEED the MadWiFi Driver..  (well you may not need it; but i found it much easier then trying NDISwrapper or anything)

The only problem is that he is trying to get a Dell Broadcom-based adapter working, not the normal atheros-based card.

I was thinking about this last night though, how did you end up with a MBP without an airport card?

---

### Post by maluka on 2007-07-09
> The only problem is that he is trying to get a Dell Broadcom-based adapter working, not the normal atheros-based card.

I was thinking about this last night though, how did you end up with a MBP without an airport card?

i changed my macbook pro's wifi card to an N-enabled card myself.

---

### Post by benanzo on 2007-07-09
Did you change the wireless card at the time you purchased it or is it external?  I wasn't aware that Apple shipped the N-enabled cards on the Core Duos.  Just the Core 2 Duos.  Did you buy a mini PCI-E card and perform the upgrade yourself?


Can you connect to the internet via ethernet while in Ubuntu?  If so open a terminal and do:
```
sudo update-pciids
```
That will update the information for your hardware.

Even if you can't connect to the internet do this:
```
lspci | grep Broadcom
```
If that doesn't return anything do:
```
lspci | grep Atheros
```

Post the output back here.  That will help in determining the chipset so you can get help installing a driver.  I'm thinking you've got a Broadcom wireless card.  You'll need to either use ndiswrapper or bcm43xx.

---

### Post by maluka on 2007-07-12
> maluka@ubuntu:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
maluka@ubuntu:~$ lspci | grep Atheros
maluka@ubuntu:~$ 

that is what i get back. i'm connected to the net via ethernet. the card i bought and installed is a Dell Wireless 1500 Draft 802.11n Mini PCI-Express-Card

on my os x 10.5 partition the card is working perfectly.

---

### Post by cyberdork33 on 2007-07-12
you are going to have to use the Dell Windows Driver and ndiswrapper to get that card working under ubuntu. It is essentially the same chip as the n series airport cards.

---

### Post by maluka on 2007-07-12
i know, i'm trying this method right now: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092). i will report back later.

---

### Post by asgard123 on 2007-07-18
> **NickFury said:**
> 

If you have a regular Core Duo (note: not C2D) then wireless should already be working

Hi All,

I have a macbook pro, 2.16 core duo and I can't seem to get the wireless card working. I am very new to linux (ubuntu in particular) so I am pretty stuck. 

From a dmesg I get this which seemed to indicate that I had IPv6 running but I have since disabled v6.

dmesg reports the following

[   40.540000] ath0: no IPv6 routers presentt
[  530.364000] spurious 8259A interrupt: IRQ7.
[ 2058.376000] applesmc: wait status failed: c != 8
[ 3980.416000] applesmc: wait status failed: c != 8
[ 4896.456000] applesmc: wait status failed: c != 8
[ 5212.468000] applesmc: wait status failed: c != 8

The driver seems to be correct and I cannot find anything on the forum that exactly fits the problem.

Any ideas?

This is the output from "iwconfig"

ath0      IEEE 802.11g  ESSID:"wlan-ap"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:04:ED:42:73:E7   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/94  Signal level=-41 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


this is the output from "iwlist scan"

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:17:9A:64:D2:B5
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/94  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:04:ED:42:73:E7
                    ESSID:"wlan-ap"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/94  Signal level=-42 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  


Thanks and I hope someone has some clues

---

### Post by cyberdork33 on 2007-07-18
From your posted information it would seem that the WiFi card is working...

ath0 is the wifi card. If you run 'iwlist ath0 scan' then the card scans for APs and gives you the output you posted. (It sees two APs). This would indicate that ubuntu can see and use the card just fine.

---

### Post by asgard123 on 2007-07-18
> **cyberdork33 said:**
> From your posted information it would seem that the WiFi card is working...

ath0 is the wifi card. If you run 'iwlist ath0 scan' then the card scans for APs and gives you the output you posted. (It sees two APs). This would indicate that ubuntu can see and use the card just fine.

Yes the card is recognised but it does not get an address via dhcp and if I put a static address in, then I still cannot surf. Eth0 is working fine but but is not a solution I can live with.

I orginally thought it was polling the modem/router for an IPV6 address which cannot be delivered as I have a small block of IPV4 on the inside.

I wondered how it would go if I uninstalled the driver and reinstalled it. However I have no real idea how I might uninstall it and haven't found much info on that subject.

---

### Post by cyberdork33 on 2007-07-18
> **asgard123 said:**
> I wondered how it would go if I uninstalled the driver and reinstalled it. However I have no real idea how I might uninstall it and haven't found much info on that subject.

I am pretty sure it has nothing to do with the driver since, well , it is working. The IP6 stuff shouldn't be an issue as IP4 will also work.

Are you using network manager? It seems that you are using a WPA protected access point so you have to make a wireless connection to the router / AP before you can do anything with DHCP, which means that it needs your network key and stuff.

---

### Post by benanzo on 2007-07-18
The driver will always look for an IPv6 router.  But it will default to IPv4 for compatibility.  Don't be alarmed when you see the "No IPv6 routers present" error in *dmesg*, that is normal.

As *cyberdork* said, your wireless card is working just fine.  You seem to be getting hung up on the authentication portion of establishing a connection.  The easiest way to connect to a WEP or WPA encrypted network is with **NetworkManager**, which is the little networking applet in the system tray (by the clock.)  If you click that do you see a drop-down list of wireless APs?  you should.  Try it without having the ethernet plugged in (I have been caught by a bug or two that prevented my wifi from polling for new aps if I was connected to ethernet, which could be a good thing?...not for me though.)

---

### Post by asgard123 on 2007-07-18
Hi again and thanks for all your help.

It seems that my modem/router (billion) is not compatable with some part of the encryption method, regardless of whether I use 128 or or 64 bit wep. The only way I can seem to get it to connected is to disable wep authentication in the modem entirely.
So for now I have reconfigured all the other pcs on the network for no encryption and everything is working. In the meantime I will work on the problem and if I turn up anything I will post it.

cheers

---

### Post by asgard123 on 2007-07-19
Hi all,

this is the fix I found for the problem with the encryption. 

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by cyberdork33 on 2007-07-19
> **asgard123 said:**
> Hi all,

this is the fix I found for the problem with the encryption. 

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

All of that is supposed to be included with Ubuntu now by default. Either way, glad you got it under control.

---

### Post by maluka on 2007-08-26
i can report that my wifi is now working. 

i installed compiz-fusion but was unable to run it. must be something to do with my ATI card

after trying for about a week and still getting this message: 'compiz (core) - Fatal: No composite extension' after trying to run it, i have given up. guess i will need to wait till betetr ATI support arrives!

---

### Post by cyberdork33 on 2007-08-26
> **maluka said:**
> i can report that my wifi is now working. 

i installed compiz-fusion but was unable to run it. must be something to do with my ATI card

after trying for about a week and still getting this message: 'compiz (core) - Fatal: No composite extension' after trying to run it, i have given up. guess i will need to wait till betetr ATI support arrives!
ATI is special, you have to use XGL because there is no compositing support in the driver. Look for a sepcific tutorial on installing with ATI, XGL, and Compiz-fusion.

---

### Post by maluka on 2007-08-27
thanks. i will give it a go.

---

