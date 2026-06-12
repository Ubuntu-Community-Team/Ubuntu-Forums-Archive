---
title: "Wireless and Graphic Card problems"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Knight of Cydonia on 2007-02-09
I've just installed ubuntu the day before yesterday, and although I'm fairly impressed, I'm also rather enervated, 'cause I've been trying to get access to my house's wireless network for 2 days now and all to no avail, I CAN'T continue to keep on using a cable, simply because of the location of the router (with built-in switches, so theoretically I could, as long as I stay near the router or plant metres of wires throughout the house, but that wouldn't be very practical), I've already sought help on the dutch ubuntu forums, and though they did help me amongst other things with getting a temporary video card driver that at least gives me something else than a black screen, I still haven't got the solutions I really need.

I have an Acer Aspire 1694, with a Broadcom network card of the type BCM5788, and an ATI mobility Radeon X700 128MB (and yes I am aware that those are apparently the worst possible combination when it comes to running Ubuntu).

My first priority of course is getting wireless drivers, I've already messed around a bit with the linux drivers I found on the Broadcom site (hey at least they provided them), and with a program called ndiswrapper, but for as already mentioned, with no results.

If I need to provide extra information on my system I'll happily do so, as long as I can get the necessary help, 'cause without wireless internet access, ubuntu is going to be of very little use to me (well at home at least, at the dorms I have cable).

For the moment I have a dual-boot, and I'm planning on keeping it that way, I still have software which doesn't run on linux, and heaps of files I have yet to find a way for even simpy opening/running them under ubuntu. (mp3-support?, I was thinking to use the Automatix package, but first things first, wireless internet access and then the rest.) :-k

---

### Post by zvezdogled on 2007-02-09
Could u post the output of lspci and iwconfig.

---

### Post by Knight of Cydonia on 2007-02-09
> **zvezdogled said:**
> Could u post the output of lspci and iwconfig.

The output respectively is:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)


> root@ubuntu:/home/stefan# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      unassociated  ESSID:"USR5461"  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:5368-6164-6F77-6661-7800-0000-00   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


As you can probably see I've already messed around myself quite a bit, since the name of my house's router is in there. I'm thinking however that isn't the same as it's ESSID however... I just remembered it from those annoying Windows balloons which pop up each time I have a connection with it from Windows XP... :)

---

### Post by aberry5555 on 2007-02-09
concerning the ATI drivers Im guessing the dutch site told you to use "vesa" instead of "ATI". You should try "radeon" instead of vesa and see if these give you better graphics.

---

### Post by -Ghost9- on 2007-02-09
I dunno about the wireless stuff, but I have an ati card(x850xt) that i recently got working.
These instructions are what finally got me up and running with 3D capabilities. 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

---

### Post by shane634 on 2007-02-09
Take a look at this thread and see if it helps:

[http://www.ubuntuforums.org/showthread.php?t=90516&highlight=BCM5788](http://www.ubuntuforums.org/showthread.php?t=90516&highlight=BCM5788)

  They have the same cards and got it working by disabling ACPI.  Good Luck

---

### Post by zvezdogled on 2007-02-09
i am no expert but this line:
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
says that you have Intel wireless card.?
06:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03) 
and, if i am not mistaking, this line says that BCM5788 is your ethernet(wired lan card).
Just for fun try to connect to the router. Write in terminal :
> 
sudo dhclient3 eth0

That should work if you have no encription on your wireless network.

Could you please report back if that worked or not. And add the output of 
> iwlist scan (if it didn't work)

---

### Post by Knight of Cydonia on 2007-02-09
Ok, sorry for the late reply, I'm still not online with Ubuntu, even though I managed too install the drivers from the Broadcom site and with some help from the dutch ubuntu forums. :confused: 

> root@ubuntu:/home/stefan# sudo dhclient3 eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:15:00:01:1d:f6
Sending on   LPF/eth0/00:15:00:01:1d:f6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@ubuntu:/home/stefan# iwlist scan
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:C0:49:FF:12:98
                    ESSID:"USR5461"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-66 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 24ms ago

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


---

### Post by zvezdogled on 2007-02-09
I see you have a wpa encrypted wireless network. In that case u need an wpa_supplicant in order to connect on your wireless network...

My guess is that your card is working as it should and that you only need a wpasupplicant to connect on your network. 
The foolproof way of testing, if i am right, is, to simply try to log on on an non encrypted network, (sudo dhclient3 eth0).

Please report back your findings and or questions.

---

### Post by r4ik on 2007-02-09
For you're graphics,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by Knight of Cydonia on 2007-02-10
> **zvezdogled said:**
> I see you have a wpa encrypted wireless network. In that case u need an wpa_supplicant in order to connect on your wireless network...

My guess is that your card is working as it should and that you only need a wpasupplicant to connect on your network. 
The foolproof way of testing, if i am right, is, to simply try to log on on an non encrypted network, (sudo dhclient3 eth0).

Please report back your findings and or questions.
Again sorry for the late reply, but getting access to wired network isn't always possible.
```
root@ubuntu:/home/stefan# sudo dhclient3 eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:00:01:1d:f6
Sending on   LPF/eth0/00:15:00:01:1d:f6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
I followed a few other guides in hopes of getting my wireless working, so far I apparently only succeeded in making the led on the front of my laptop which is supposed to be linked to whether wifi is on or off, blink...
:confused: I also installed a network manager in the hope that it would detect the network, all to no avail.

I have downloaded the drivers for the intel pro/wireless 2200 BG from the intel site and sourceforge, but I'm still reading the install guides, which unfortunately require a knowledge of Linux beyond mine...

---

### Post by zvezdogled on 2007-02-10
Now i am sure. Your card is intel pro/wireless 2200 BG which is good because they are natively supported by Ubuntu and share fact that you got sth like this

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

shows that your device is there and working.

No DHCPOFFERS received. means that there was no open network, you wanted to log on an encrypted network or there are no networks around you...

what are your network settings. If you have wpa encription try using wpasupplicant to logg on.
This is not easy way but the only way, i know of, to log on wpa network. 
check this:
[http://www.ubuntuforums.org/showthread.php?t=263136]("http://www.ubuntuforums.org/showthread.php?t=263136")

---

