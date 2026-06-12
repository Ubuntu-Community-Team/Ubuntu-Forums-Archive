---
title: "Wireless on Dell Laptop"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-12-15
New to Ubuntu and loving it! 

I have a Dell Inspiron 1300 laptop with Gutsy 7.10 installed.

1) Installed Network Manager

2) Installed Firmware for Broadcom 43xx chipset family (from Restricted Drivers)
   -when prompted for "Specify formware location", I use the one downloaded from the internet at [http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)

3) From there, i can select my network (ie. machado), which prompts for network key.
   -i'm using a simple WEP 64bit hex encryption on my linksys router.

After logging in and establishing a connection with the router, i'm still unable to access any sites using firefox or any other internet applications.

Tthe following is what I get when running iwconfig
> tony@tony-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"machado"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:18:F8:1A:1A:5A   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=51/100  Signal level=-62 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:10  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tony@tony-laptop:~$ 


The following is what I get when I run ifconfig
> tony@tony-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:91:6B:7D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:56:62:83  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe56:6283/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71 errors:0 dropped:576 overruns:0 frame:0
          TX packets:1054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7800 (7.6 KB)  TX bytes:53347 (52.0 KB)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2800 (2.7 KB)  TX bytes:2800 (2.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.59.1  Bcast:192.168.59.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.121.1  Bcast:172.16.121.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tony@tony-laptop:~$ 


I would really, really, really appreciate some help here :)

---

### Post by tonycm1 on 2007-12-15
I just tried removing encryption on the router and it's still not working.

My other laptop with XP is running fine though so it's not a router/isp problem.

---

### Post by tonycm1 on 2007-12-15
bump.

---

### Post by chunder4160 on 2007-12-15
Persevere! BCM43xx does work. I spent around 4 hours fiddling with the settings on my Dell Latitude 110L yesterday following the guidance set out here [http://ubuntuforums.org/showthread.php?t=201902]("http://ubuntuforums.org/showthread.php?t=201902"). It wasn't necessary to install ndiswrapper and I uninstalled it in the end. Although I could see my AP, I couldn't connect until I rechecked the MAC code for my wireless card and found that I had entered it onto the router with one digit incorrect. I also found the guidance set out here really helpful: [http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by Papa-san on 2007-12-15
The wireless link in my signature line has a link to a good comprehensive and nOOb friendly how-to...
I will also recommend a program called "WICD" which has made my life SO much easier. You can google it to find the right place to download it...

---

### Post by tonycm1 on 2007-12-15
Alright... there's been a little bit of progress on my front.

Following some advice from both chunder4160 (thanks for the encouragement) and Papa-san, I've been picking away at this for a few hours now. This is what i've done to get it "partially" working:

Went to:
[http://www.linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://www.linuxwireless.org/en/users/Drivers/b43#devicefirmware)
and downloaded the most up to date firmware
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

after this, installed it using the "Restricted Driver Manager" in System/Admistration

After doing this, i was then able to see my wireless network "machado".

> tony@tony-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:F8:1A:1A:5A
                    ESSID:"machado"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-41 dBm  Noise level=-72 dBm
                    Extra: Last beacon: 152ms ago


However, even though i'm "connected", I still can't access anything in firefox or any other internet based applications (amsn etc).

Under devices in System/Administration/Network Tools, I see the following for my wireless adapter:

> 
Network device:	eth1
Hardware address:	00:14:a5:56:62:83
IP address:	192.168.1.102
Netmask:	255.255.255.0
Broadcast:	192.168.1.255
Multicast:	Enabled
MTU:	1500
Link speed:	24 Mbps
State:	Active
Transmitted packets:	479
Transmission errors:	0
Received packets:	53
Reception errors:	0
Collisions:	0


Any suggestions why I can't access the internet? I've tried with my other laptop (running windows xp) and the wireless connection works fine.

:confused:

---

### Post by tonycm1 on 2007-12-15
I just tried connecting to my network (connected successfully) and then pinging myself

> tony@tony-laptop:~$ ping 192.168.1.102
PING 192.168.1.102 (192.168.1.102) 56(84) bytes of data.
64 bytes from 192.168.1.102: icmp_seq=1 ttl=64 time=0.034 ms
64 bytes from 192.168.1.102: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 192.168.1.102: icmp_seq=3 ttl=64 time=0.036 ms
64 bytes from 192.168.1.102: icmp_seq=4 ttl=64 time=0.035 ms


Worked great!.... THEN, i tried pinging my other computer (running on Ubuntu with a wired connection)

> tony@tony-laptop:~$ ping 192.168.1.104
PING 192.168.1.104 (192.168.1.104) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=1 Destination Host Unreachable
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable


which didn't work.... so if I can't even connect to another computer on the router, then there is definitely a problem.

Ideas? :confused:

---

### Post by dstew on 2007-12-15
Maybe it is your DNS. In your setup, did you specify a DNS address?

---

### Post by chunder4160 on 2007-12-16
I did read in one of the many posts on setting up wireless that the cards could be fussy about the channel and seemed to prefer channel 11 - I see that you are set to channel 6. Try changing the channel to 11 and see if that makes any difference. I also had to enable my card for roaming mode before it would let me connect - have you tried that?

---

### Post by tonycm1 on 2007-12-18
I verified that the DNS settings were the correct ones... even tried removing them, but that didn't work.

I then tried to set my router to channel 11 with NO encryption and was still unable to get this working.

Finally, I got so frustrated with this Broadcom 4318 (BCM4318) built in wireless card on my laptop that I tested a USB wireless device that I have and was able to pop onto my router as easy as "plug-and-play"... 

That really frustrated me.. lol.

I really do want to get my internal card working though but have really run out of options... i've tried ubuntu / kubuntu / xubuntu... they all produce the same problems.

Any ideas?

---

### Post by anewguy on 2007-12-18
Personally, I've seen too many reports of problems trying to use the restricted driver with the firmware.  Your best bet to get the wireless working itself is to just install ndiswrapper and it's utilities, blacklist the existing bcm43xx driver, then use ndiswrapper to install the windows driver for your wireless card.  Specific instructions for that are in several places on the forum, but I would suggest you start with a pre-compiled version of ndiswrapper first.  Many of the posts want you to download the source and compile it, while I've never had any problems just using the ndiswrapper and utilities that are in the synaptic package manager.  

Here is a link (keeping in mind that starting I believe with Feisty (7.04) you will have to install ndiswrapper and it's utils via the net, not from CD):

[http://ubuntuforums.org/showthread.php?t=507505&highlight=Gateway+mx3215](http://ubuntuforums.org/showthread.php?t=507505&highlight=Gateway+mx3215)  

Just read through the section on getting the wireless working and you should be able to do it with no problem.  Go ahead and download the driver it recommends, as it is the generic windows version.

Post back if you have more problems!   We can work on seeing the other stuff on the net after that.:)

---

