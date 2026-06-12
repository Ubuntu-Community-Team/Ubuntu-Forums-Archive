---
title: "Wireless set up issues"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by andybleaden on 2008-02-04
Hi I have a d link wireless card and log on to my neighbours wireless router ( with his permission before you ask!) 

It was a fiddle to set up under feisty as the card was unsupported but we have got it running with with a wireless programme that logs in with a password ...however I tried recently to set up my own home system and really ran into problems with my own router as I could not set it up via linux.

Is there an easier piece of software that I can use to do this. I could 'see' the router but could not connect to it.

Any help would be gratefully received

---

### Post by aeiah on 2008-02-04
what is your new router? does it have a WPA or WEP mode that it defaults to initially? if so, the information should be provided for getting online. 

the easiest thing to do would probably be to login to your router's control panel via ethernet and turn the wireless encryption off and see if you can connect, then if that works, set it to WPA PSK (if your linux drivers support WPA). some routers dont let you login to the admin panel via wireless for security reasons, even if you are authenticated

---

### Post by jan quark on 2008-02-04
some input would be nice

please post the results of the following terminal commands while being in the range of your home wireless

```
iwconfig
```

```
ifconfig
```

```
sudo iwlist scan
```

```
lspci
```

```
lshw -C network
```

thank you

---

### Post by andybleaden on 2008-02-04
Will do this as soon as I can and post the results on here. Many thanks...I have also had to send the broadband router back as it was not working even on a windows thing when connected but need to sort this out properly. Will stick results on when I get home and online.

---

### Post by andybleaden on 2008-02-04
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b linked  ESSID:"fishpond"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:D8:1F:08
          Bit Rate=11 Mb/s   Sensitivity=80/85
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-41 dBm  Noise level=-251 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      Link encap:Ethernet  HWaddr 00:50:8D:61:B4:08
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xec00

if config 

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:804 (804.0 b)  TX bytes:804 (804.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0D:88:3F:2D:37
          inet addr:10.0.0.51  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:88ff:fe3f:2d37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4318 errors:0 dropped:1 overruns:0 frame:0
          TX packets:3666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5176966 (4.9 MB)  TX bytes:488610 (477.1 KB)
          Interrupt:19 Memory:f8954000-f8954100

andy@andy-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:D8:1F:08
                    ESSID:"fishpond"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality:144  Signal level:0  Noise level:32
                    Extra: Last beacon: 324ms ago
          Cell 02 - Address: A2:2E:77:3A:C7:90
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality:201  Signal level:0  Noise level:90
                    Extra: Last beacon: 81ms ago


00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Ethernet controller: D-Link System Inc DWL-510 2.4GHz Wireless PCI Adapter (rev 20)
00:0a.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

andy@andy-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: DWL-510 2.4GHz Wireless PCI Adapter
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 20
       serial: 00:0d:88:3f:2d:37
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=10.0.0.51 latency=32 maxlatency=64 mingnt=32 module=r8180 multicast=yes wireless=802.11b linked
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:50:8d:61:b4:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
andy@andy-desktop:~$                           


Any wiser>>>?

---

### Post by andybleaden on 2008-02-05
bump?

Any ideas anyone?

---

### Post by andybleaden on 2008-02-11
Up for air ...any ideas

---

### Post by Gigamo on 2008-02-11
Are you using Network Manager? If so, I would suggest trying out Wicd, found here: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by andybleaden on 2008-02-11
I will have a look into this and try this later at home

---

