---
title: "wireless dropout/wireless channel change"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by erutufon on 2008-01-28
hello
my problem is an intermitant dropout of the wireless connection.
I am using a belkin 802.11g wireless usb stick, and the router is a netgear adsl dg834gt.  I am using ubuntu 7.10.

the connection works on startup some of the time, and rebooting solves the problem some of the time.  my computer can see the connection, as well as my neighbours wireless connections.  i have a cordless phone also.

having looked through the forum it looks like the phone could be the problem, maybe I need to change the wireless channel.  however i am linux newbie and confused by a lot of the jargon, and don't know how to do this.  

if i click on the network tab in the admin menu I get a list of connection options, but I cannot tick the wireless box (don't know if this is relevant). roaming mode is enabled on the network settings.

does anyone know how to fix this, and is there any program I can download that will do it all for me?  

many thanks

---

### Post by jan quark on 2008-01-28
first some input
run the following commands in the terminal
dont cry wont be that hard :)

just type it into the terminal and enter

iwconfig
ifconfig
lspci
sudo iwlist scan < after this command you have to type in your login password

this commands will show additional pieces of information about your network status

by the way have you tried to set the roaming mode of and configure the network settings manually, it help me with some issues to do so

---

### Post by bump_ on 2008-01-28
Changing the channel is very simple

```
sudo iwconfig wlan0 channel 8
```

Just type than into the terminal and replace "wlan0" with your wireless interface and "8" with whatever channel.

It may also help to see if your phone operates at a similar frequency to your current one. Wireless phones usually have the frequency they use written on them somewhere and you can find the frequency your wireless internet is using by typing 

```
iwconfig
```
into the terminal and looking under your wireless interface.

Hope it helps

---

### Post by ~vel on 2008-01-28
I'm having the same Problem, Network card is a Netgear WG111v2. Here's my results for running your suggested commands jan quark.

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ACTIONTEC"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:B3:12:27:21   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=44/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:7E:CD:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:91:F1:37  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe91:f137/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14322 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18583822 (17.7 MB)  TX bytes:1186632 (1.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-B5-91-F1-37-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
lspcii

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:06.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:06.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

sudo iwlist scan 

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:50:33:96
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=46/100  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000050ef57992f
```
also, i've tried to turn off roaming mode and configure it manually but i don't use WEP or WPA and it always tries to use one of those two encryptions and won't let me hit ok without a password, so that could just as easily be the problem. Also it should probably be noted that I have my router set up to accept only certain MAC addresses.

---

### Post by bump_ on 2008-01-28
~vel,

I think you are on the wrong channel. 
from your iwconfig:
> Frequency:2.452 GHz
That is channel 9

from your iwlist:
> Channel:6

Try typing 

```
sudo iwconfig wlan0 channel 6
```

restart your connection and see what happens

---

### Post by ~vel on 2008-01-28
Eh, it's definitely channel 9, that's what I have my router set to (ACTIONTEC). Other ideas? =(

Ah, wait, I see what you're getting at. I did that and the thing dropped on me while i was doing that test, here, I'll re-do it and edit it in the post, give me a moment.

```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:50:33:96
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=34/100  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000515c746186
          Cell 02 - Address: 00:0F:B3:12:27:21
                    ESSID:"ACTIONTEC"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz
                    Signal level=72/100  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000022aa5e9e7f
```

Interestingly enough, it seems to happen when I'm trying to browse Myspace and Facebook. Maybe it somehow has something to do with having a bunch of requests at once?

I end up resolving the issue by unplugging my dongle> letting it sit for about 5 seconds> plugging it back in> left clicking on network manager> connect to other wireless network> then entering in ACTIONTEC and hitting ok.

---

### Post by ~vel on 2008-01-28
bump

---

### Post by bump_ on 2008-01-28
Ahh that second part with ACTIONTEC was missing from your first iwlist. The channel discrepancy was just something I noticed in your first post. I have no idea what is actually wrong now.

---

### Post by ~vel on 2008-01-28
=( Thanks for you input anyways.

---

### Post by erutufon on 2008-01-29
hi jan quark
I have tried turning off roaming mode, then setting network settings manually.  this disconnected the internet (i typed in the network name and set configuration to dhcp).

running the commands you recommended I get the following;
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:6D:4B:CA   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:19:D1:47:32:C6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xecc0 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:49:31:12  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe49:3112/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1068576 (1.0 MB)  TX bytes:160085 (156.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-49-31-12-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lspci:

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)

sudo iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:6C:6D:4B:CA
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-70 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000012f3a1cc6d

afraid this looks like a foreign language to me..:)
thanks for your help

---

