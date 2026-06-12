---
title: "[SOLVED] Wireless connections"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Phil Binner on 2008-02-16
Hi

I am very new to Ubuntu. I have just got the system up and runing, and have attached a wireless network adaptor. I assume the sequence of events is - attach adaptor, install adaptor, attach to network, browse internet, but I'm stuck at the first hurdle. How do I see my wireless adaptor to install the drivers.

Phil B

---

### Post by jan quark on 2008-02-16
good starting point is here

[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)



and please run 
```

lspci
```

and 
```

sudo lshw -C network
```

in terminal and post the output
this will help to determine the specific model of your wlan card

---

### Post by Phil Binner on 2008-02-16
Thanks for that, but I'm newer than you thought. How do I open a terminal. I assume it's like a command prompt, but where is it.

---

### Post by Phil Binner on 2008-02-16
Sorry, ignore the last post, I found the terminal prompt. I'll get all the info I can, including what's written on the card.

---

### Post by Phil Binner on 2008-02-16
Jan

The device is a Belkin PCI card F5D7000. 

Response to the command lspci -v | less     was

00:0b.0 Network Controller: RaLink RT2500 802.11g Cardbus/mini PCI (rev 01)
Subsystem: Belkin F5D7000 wireless G desktop network card
Flags: bus master, slow devsel, latency 64, IRQ 21
Memory at ff6f8000 (32 bit, non prefetchable) [size=8K]
Capabilities: <access denied>

There was a long response to teh command sudo lshw -C network. The bit which may help is 

Configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g

cheers

---

### Post by Phil Binner on 2008-02-16
I seem to be moving on, but in a one step forward and 2 steps back mode. I found a section called WifiDocs/Device/F5D7000 in the Ubuntu documentation. This gives different instructions for versions 1 and 3 of the card, version 3 having the RT2500 chipset. using previous commands I found I had version 1, but the chipset is RT2500, so which should I run. I decided that I could always try again, so I followed instructions for version 1. I downloaded the file bcmwl5a.inf and tried to load it using the command sudo ndiswrapper -i <bcmwl5a.inf> . I got the message sudo: ndiswrapper: command not found. Where do I go from here please???

---

### Post by MasterJS on 2008-02-16
Do you have Ubuntu Gutsy Gibbon 7.10? If you do, you might need the restricted drivers. You can get them by going to SYSTEM > ADMINISTRATIOn > RESTRICTED DRIVERS MANAGER and selecting the drivers for your device (if there are any)

---

### Post by Phil Binner on 2008-02-17
Thanks, I do have Gutsy Gibbon 7.10, but when I did this I was told > your hardware doew not need any restricted drivers. I'm not actually sure that the device is not already active, because when I drill down through places I get Network and then Windows Network. I can't see why Windows Network should be part of Ubuntu, and there is a windows network out there. I can't get onto the internet,though, and the network name (Home) and contents do not show, even though I temporarily disabled the rest of the networks firewall. Also, when I look att eh properties of Windows Network it says it's a 'desktop configuration file'. Could it be that the wireless card is active but Obuntu's firewall is blocking me? Where do I look to confirm any of this?

---

### Post by jan quark on 2008-02-17
> Configuration: broadcast=yes driver=rt2500pci latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g

hmm your card seems to be recognized by ubuntu

please run these commands and post the output please

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
cat /etc/network/interfaces
```

---

### Post by Phil Binner on 2008-02-18
Having run the commands you gave I think I have been asking the wrong questions. I seem to be able to see the network, so the WLAN card must be working. I'm still not sure whether I'm actually connected though. I can't see anything on the network and other computers cant see Ubunto.

I've been expecting to find something like the Windows way of detecting a network and connecting to it, and then being told if your successful. Perhaps that's where I'm going wrong. What I did do, however, was go into manual setup and enter what I think are the network settings, and then I put the router into pairing mode. How do I tell if I'm connected.

The results of the commands  was:

bigbin@Ubuntu:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11g  ESSID:"Livebox-C890"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:26:36:34:B2   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
bigbin@Ubuntu:~$ 
bigbin@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:53:A8:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xe400 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17112 (16.7 KB)  TX bytes:17112 (16.7 KB)
wlan0     Link encap:Ethernet  HWaddr 00:11:50:14:D7:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
wlan0:ava Link encap:Ethernet  HWaddr 00:11:50:14:D7:76  
          inet addr:169.254.6.152  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-14-D7-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
bigbin@Ubuntu:~$ sudo iwlist scan
[sudo] password for bigbin:
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:1C:26:36:34:B2
                    ESSID:"Livebox-C890"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Signal level=-63 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000004eb68b47d3
bigbin@Ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wireless-key 2FA4EB84F96171E8
wireless-essid Livebox-C890
auto wlan00

Thanks

---

### Post by Phil Binner on 2008-02-19
Going through the documentation I notice that I should have a 'Network Manager'. I have a 'Manual network configuration' icon in the notification area, but no network manager. Is this my problem. I have gone through the manual setup for my router, and ticked the box, but it's difficult to know whether I got everything right without a dialogue.

---

