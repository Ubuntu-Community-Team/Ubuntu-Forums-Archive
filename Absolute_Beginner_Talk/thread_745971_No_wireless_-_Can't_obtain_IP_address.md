---
title: "No wireless - Can't obtain IP address"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by CamCollie on 2008-04-05
I have been using 7.10 for a week and am loving it. The only problem I have is that I can't connect to the internet via wireless. I tried Network Manager with no luck and am now using  WICD but it still isn't working,

My specs

Dell 6400 Notebook Intel Core 2 Duo - 2Ghz  / 2G RAM / Radeon X1400 / 120G HDD
Intel PROSET Wireless / Netcomm NB5+4 Modem/Router

IWCONIFG :

[QUOTE]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"wireless"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:01:38:8C:0E:8B   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20742   Missed beacon:0

[QUOTE]

IFCONFIG:

[QUOTE]eth0      Link encap:Ethernet  HWaddr 00:15:C5:CD:F1:4A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:275995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:317547458 (302.8 MB)  TX bytes:22059348 (21.0 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:02:45:A3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:20885 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:efcff000-efcfffff 

eth1:avah Link encap:Ethernet  HWaddr 00:19:D2:02:45:A3  
          inet addr:169.254.6.7  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:efcff000-efcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7783 (7.6 KB)  TX bytes:7783 (7.6 KB)
[QUOTE]

WICD can connect using a wired connection and see my SSID and others. Wd my Wifi when I try and connect to my SSID it just says "Obtaining IP address" and then fails. And my wifi LED is blinking rapidly.

If anyone could walk me through what I have to do it would be greatly appreciated. I'm a noob so go easy on me :)

Thank you

---

### Post by m60dude5 on 2008-04-05
Do you have a static IP? Or is it assigned automatically? Have you tried editing the settings under manual connection? There are a bunch of tabs in there. Add your router's IP and your IP to the wireless properties dialog. Then try to connect again. Let me know if it works, I had similar problems when I first installed.

---

### Post by CamCollie on 2008-04-05
Thanks for the help.

I have set up the static IP in the manual settings in WICD and when I clicked connect it said that it was connected to my SSID. Except I still cannot access the internet. Pages just simply won't load.

---

### Post by Helios1276 on 2008-04-05
We are not so differnet you and I, search for the thread 'wanting wireless'..it's frustrating as hell! If I get any ideas I'll send them your way and good luck!:popcorn:

---

### Post by CamCollie on 2008-04-06
And I meant to mention that I am using the 64 bit version of 7.10 if that makes any difference...

---

### Post by ghost_ryder35 on 2008-04-06
try using Network Manager and assigning a static IP with your current configuration scheme,
i.e.
IP address: 192.168.1.10
Broadcast: 192.168.1.255
Subnet mask: 255.255.255.0
Default Gateway: 192.168.1.1
DNS servers: 192.168.1.1, 4.2.2.1 , 4.2.2.5

---

### Post by ghost_ryder35 on 2008-04-06
You can also do this in the terminal like so:
on the server edit the interfaces file to get a static ip
```
sudo vi /etc/network/interfaces
``` 
 
you will see
```

auto eth0  ##you need to do this to whatever interface you need to apply the static IP too.  In this example we will assume it is the most common one "eth0"
iface eth0 inet dhcp

```
 
change it to
```

auto eth0
iface eth0 inet static
        address 192.168.1.10  * ##whatever you want you ip address to be*
        netmask 255.255.255.0  *## your subnet mask*
        network 192.168.1.0    * ##your network address*
        broadcast 192.168.1.255  *##broadcast will always be the last ip address of the subnet range*
        gateway 192.168.1.1  *##your routers address*

```
 
A "vi" cheat sheet [http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

---

### Post by CamCollie on 2008-04-06
> **ghost_ryder35 said:**
> You can also do this in the terminal like so:
on the server edit the interfaces file to get a static ip
```
sudo vi /etc/network/interfaces
``` 
 
When I do that I get this

[QUOTE]auto lo
iface lo inet loopback



iface eth1 inet dhcp
wpa-psk 8e1d33a4b7bd11032401092a5d847db898713d5b00f8e84c465f5d0e734c85a4
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid wireless

auto eth1
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/network/interfaces" 13 lines, 208 characters



Am I doing something wrong? Thanks for all your help so far :)

---

### Post by CamCollie on 2008-04-09
Anyone?

---

### Post by CamCollie on 2008-04-15
Bump

---

