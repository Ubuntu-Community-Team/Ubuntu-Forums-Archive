---
title: "ANOTHER &quot;Problems with wireless and Ubuntu&quot;  post"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by ThePinkWitch on 2008-02-07
I have been "messing" with trying to get my wireless network to work for days now. I got really excited a couple of days ago because it actually connected and I thought i'd licked the problem. HAH!!! After re-installing Ubuntu five times in the last few days I realise now it was just messing with my head. ok..when I first boot up the machine it will connect after quite a while. It connects for a couple of minutes then disconnects. The blue connection symbol merrily circles around then freezes. If I try to click on anything at all after that it will say on the bottom taskbar eg loading blah blah..then it stops ..nothing works. I can't get anything to open. I'm wondering if maybe the computer has a problem now. Maybe lack of RAM would cause that? It only has 196mg  which is an odd number for RAM.  Installing updates and up grades etc is just too hard without internet. Any more ideas?? I'm about to call it quits. Thanks.:)

---

### Post by jan quark on 2008-02-07
some more info would be nice

pls post the output of the following terminal commands

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

lshw -C network
```

```
lspci
```

---

### Post by ThePinkWitch on 2008-02-07
kayte@kayte:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kayte@kayte:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:CC:77:37:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:4D:19:CB:B1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-4D-19-CB-B1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

kayte@kayte:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:A3:F0:80:41
                    ESSID:"Home"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz
                    Quality=52/64  Signal level=33/65  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000008373a2024

kayte@kayte:~$ lshw -c network
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status

kayte@kayte:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:0c.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0e.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)
kayte@kayte:~$ 

Sorry. I didn't really know how to do that I hope this is right. I had to get if from the other computer onto this one and wasn't sure how to get the terminal stuff. Anyway I hope you can make some sense of this and thankyou :)

---

### Post by jan quark on 2008-02-07
for the future

linux is case sensitive so when I write 

```
lshw -C network
```

I really mean a capital C :)

and please post also the output from

```
lsusb
```

you can copy and paste the output with ctrl +c and ctrl + v to a text file

---

### Post by lswest on 2008-02-07
what you can try is giving in ```
sudo iwconfig wlan0 essid Home key [your wireless key here]
``` and then run ```
sudo iwconfig
``` again to make sure the changes were applied to the card (if it wasn't, you have a driver issue, and we need to work on that then) and if it was, try to get an IP with ```
sudo dhclient wlan0
``` Hope this helps, because, imho, i don't think the network manager is very good in Ubuntu (i usually install either wicd or kwifimanager, or just do it from the terminal).  Also...the only thing the lack of ram could cause would be the freezing of the applet, but that's not the only way to connect^^

if it's a driver issue, i'll dig out my old WG111v2 drivers and see if i can get my dongle working on my computer again :P (switched over to a PCI wireless card a while back) anyways, hope it works.

---

### Post by ThePinkWitch on 2008-02-07
kayte@kayte:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 00
       serial: 00:a0:cc:77:37:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=32 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:4d:19:cb:b1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
kayte@kayte:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 002: ID 062a:0003 Creative Labs 
Bus 001 Device 001: ID 0000:0000  
kayte@kayte:~$ 

It all means nothing to me lol I hope it does to you. :mrgreen:

---

### Post by ThePinkWitch on 2008-02-07
> **lswest said:**
> what you can try is giving in ```
sudo iwconfig wlan0 essid Home key [your wireless key here]
``` and then run ```
sudo iwconfig
``` again to make sure the changes were applied to the card (if it wasn't, you have a driver issue, and we need to work on that then) and if it was, try to get an IP with ```
sudo dhclient wlan0
``` Hope this helps, because, imho, i don't think the network manager is very good in Ubuntu (i usually install either wicd or kwifimanager, or just do it from the terminal).  Also...the only thing the lack of ram could cause would be the freezing of the applet, but that's not the only way to connect^^

if it's a driver issue, i'll dig out my old WG111v2 drivers and see if i can get my dongle working on my computer again :P (switched over to a PCI wireless card a while back) anyways, hope it works.

LOL it took me half an hour to get the terminal text from the other reply onto here and now I gotta trot back and do it again. If you only knew the production it is you would crack up laughing at me. Thanks I'll go do it. :)

Oh DUH I need to go DO it not put it in here .I'm losing my mind all this network stuff lol

---

### Post by lswest on 2008-02-07
lol, sorry about that.  this > Bus 001 Device 008: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2) tells us that the card is at least being recognized, which should mean that the drivers are working :P so...my advice might end up being futile :P

P.S. how are you carting the information back and forth?  you can just run the commands, copy it to a text file, and put it on a USB stick, can't you? :P

---

### Post by jan quark on 2008-02-07
it seems you have a usb wlan dongle thingy
kayte@kayte:~$ lsusb
Bus 002 Device 001: ID 0000:0000
**_Bus 001 Device 008: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)_**
Bus 001 Device 002: ID 062a:0003 Creative Labs
Bus 001 Device 001: ID 0000:0000
kayte@kayte:~$

try this guide

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29)

---

### Post by ThePinkWitch on 2008-02-07
yep thats what I'm doing now. By key does it mean my passphrase? Or WEP key? I wrote the WEP key by hand and I'm having trouble deciding if the zeros are 0's or O's . *sigh* maybe I should just give up. Who needs internet anyway! LOL. Thanks for your help also.

---

### Post by ThePinkWitch on 2008-02-07
> **jan quark said:**
> it seems you have a usb wlan dongle thingy
kayte@kayte:~$ lsusb
Bus 002 Device 001: ID 0000:0000
**_Bus 001 Device 008: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)_**
Bus 001 Device 002: ID 062a:0003 Creative Labs
Bus 001 Device 001: ID 0000:0000
kayte@kayte:~$

try this guide

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29)

Dongle Thingy?? LMAO :lol:

---

### Post by ThePinkWitch on 2008-02-07
it's just connected now. It seems to be something to do with loopback or whatever. Localhost it's listing as connected too. I tried doing the manual config thing but it won't accept my WEP key or passphrase. AHHHHHHHH I dunno!

---

### Post by ThePinkWitch on 2008-02-07
Any ideas as to why it connects for a few minutes then disconnects and won't re connect? It seems to just slowly fade out. If you know what I mean. It  starts off at good speed then gets slower and slower and disconnects. :confused:

---

### Post by lswest on 2008-02-07
sorry i haven't replied, i was in class :P school just takes all my time XD 
anyways,  If i remember correctly, my wg111v2 didn't have the strongest connection either, frequently lost packets, but it never really disconnected.  
and yes, by key i mean WEP key, the passphrase doesn't get converted to WEP if you give it in like that.  
and loopback is just a connection onto itself (localhost=127.0.0.1=the current machine...basically, it's connecting to itself).  
does the wireless dongle get really hot? mine used to and then it was shut down because it was overheating...i'm not sure how i fixed the problem i had.  If i remember, i'll post it here^^

i just re-read that and realized it was really jumbled up, so i spaced it out a bit :P...and uh, if you're not sure what your WEP key is, it consists of the letters A-F and the numbers 0-9 (it's in HEX) so, the 0 would be a 0 and not an o ;)

---

### Post by ThePinkWitch on 2008-02-07
> **lswest said:**
> sorry i haven't replied, i was in class :P school just takes all my time XD 
anyways,  **If i remember correctly, my wg111v2 didn't have the strongest connection either, frequently lost packets, but it never really disconnected. ** 

K so that could be some of the problem


and yes, by key i mean WEP key, the passphrase doesn't get converted to WEP if you give it in like that.  
and loopback is just a connection onto itself (localhost=127.0.0.1=the current machine...basically, it's connecting to itself).  
**does the wireless dongle get really hot? mine used to and then it was shut down because it was overheating**.  yes it does.

 WEP key is, it consists of the letters A-F and the numbers 0-9 (it's in HEX) so, the 0 would be a 0 and not an o ;)

The WEP key I have starts with F but it wouldn't accept it for some reason. Any way it's connected now and it's been on for about 10 minutes. Go figure lol. But then tomorrow it will probably not connect again . Obviously if it connects the settings must be ok I guess. Maybe it is my dongle lol such a funny word. Thanks for all your help : :)

---

### Post by lswest on 2008-02-07
no problem, but it really may be a problem of the dongle getting too hot...might be able to disable the temperature sensor, but i'm not sure.  In any case...it would probably void your warranty, and may lead to your dongle melting lol

---

### Post by ThePinkWitch on 2008-02-07
> **lswest said:**
> no problem, but it really may be a problem of the dongle getting too hot...might be able to disable the temperature sensor, but i'm not sure.  In any case...it would probably void your warranty, and may lead to your dongle melting lol

 LOL god forbid! 
 I still think I've done something wrong. Instead of being one network listed in the Netgear screen on the main computer there is now 2. The original one is listed as inactive and the other one is listed a New Network. So This main computer where the network was set up originally probably has different info to what I've put in on the new computer. (which is my 2nd machine.) So i probably screwed something up lol. I'm done with it for now Thanks for all your help.

---

### Post by sneeks on 2008-02-07
hi mate,try changing your routers encryption to wpa-psk, and change channel selection from automatic to say 6,this solved all my probs with a dongle on my sons pc.
snneks

---

