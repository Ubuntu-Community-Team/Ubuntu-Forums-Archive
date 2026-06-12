---
title: "[SOLVED] [HELP] BackTrack 5 R3 Cannot connect to the internet + PICTURES"
date: 2013-12-02
forum: Any Other OS
---

### Post by adlerademov on 2013-12-02
[SIZE=2]For over 3 days now I am trying and trying to get this wireless working! I've tried almost every tutorial over the YouTube, Backtrack-linux forums, aircrack-ng forums and others.
The only one thing I haven't tried is to update the firmware for my Intel(R) Centrino(R) Wireless-N 2230 from here --> [http://wireless.kernel.org/en/users/Drivers/iwlwifi#Download](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Download) , just because I really _don't_ know how to do it.
PS: In 2 or 3 tuts I saw they launch the network simply by going to *Service --> Start Network* and then they're doing the terminal job.* I dont have that option...*[/SIZE]
[I]
_What I am talking about?_ 
[/I]Imma be honest with You guys... I've started with the tought that I want to have a dual boot laptop (Win7 + BackTrack 5 R3) , and hack WiFi passwords (that noob in me... :D)
I have to say I have experience with computers at all, WebDesign and Developing.
_What I've got?_
**Dell Inspiron 17R 5721**
With 1TB, 8GB RAM, Intel Dual Core i7-3517U, 
Internet cards (I really dont know do I have 2 of them or what?! (more on Tutorial 4)):
Intel(R) Centrino(R) Wireless-N 2230
Realtek PCIe FE Family Controller
*I am pretty sure all my Drivers are the latest running (Win 7).*

_*What have I done?*_
I've installed BackTrack 5 R3 via USB (with unetbootin). I've tried to open google.com but luck wasn't on my side.
I've been searching over the internet for like 3 days now and I can say I've tried 2 or 3 things, but I am sure there is something very SIMPLE that I am missing, this is why I am here. To search for help.

[CENTER]**And here the adventure begins...**[/CENTER]
_*What I have tried so far?*_

---------------------------------------------------------------------------------------------------------------------
[B]Tutorial 1 - [http://www.youtube.com/watch?v=1lor5rzzl1o](http://www.youtube.com/watch?v=1lor5rzzl1o)
(lately I saw the tutorial is from 2010)[/B]

```

root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ca:3a:c1:84:fa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x2000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1145 (1.1 KB)  TX bytes:1145 (1.1 KB)


root@bt:~# sudo ifconfig eth0 up
root@bt:~# sudo ifconfig eth0 192.168.0.27 netmask 255.255.255.0
root@bt:~# sudo iwconfig eth0 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth0 ; Operation not supported.
root@bt:~# 

```
Picture --> [http://imageshack.com/a/img440/5065/7749.jpg](http://imageshack.com/a/img440/5065/7749.jpg)

---------------------------------------------------------------------------------------------------------------------

**Tutorial 2: Unknown source**

```

root@bt:~# ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ca:3a:c1:84:fa  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x2000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1273 (1.2 KB)  TX bytes:1273 (1.2 KB)


root@bt:~# ifconfig eth0 up
root@bt:~# /etc/init.d/wicd start
 * Starting Network connection manager wicd                              [ OK ] 
root@bt:~# 

```
Picture --> [http://imageshack.com/a/img812/157/vt0o.jpg](http://imageshack.com/a/img812/157/vt0o.jpg)

---------------------------------------------------------------------------------------------------------------------

**Tutorial 3: Backtrack-linux forums**

```

root@bt:~# ifconfig eth0 192.168.0.27
root@bt:~# route add default gw 192.168.0.1
root@bt:~# echo nameserver 192.168.1.1. /etc/resolv.conf
nameserver 192.168.1.1. /etc/resolv.conf
root@bt:~# /etc/init.d/network start
bash: /etc/init.d/network: No such file or directory
root@bt:~# /etc/init.d/wicd start
 * Starting Network connection manager wicd                              [ OK ] 
root@bt:~# 

```
Picture --> [http://imageshack.com/a/img819/7058/4tjm.jpg](http://imageshack.com/a/img819/7058/4tjm.jpg)

---------------------------------------------------------------------------------------------------------------------

**Tutorial 4: Other forum, unknown member**

```

root@bt:~# sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: b8:ca:3a:c1:84:fa
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c1500000-c1501fff
root@bt:~# 

```
Picture --> [http://imageshack.com/a/img845/7238/xoaz.jpg](http://imageshack.com/a/img845/7238/xoaz.jpg)

---------------------------------------------------------------------------------------------------------------------

*I want to mention that the error when launching WCID was simply fixed it by:*
1.Restart BackTrack 5 R3 and _BEFORE_ launching WCID open Terminal and type:
```

1.dpkg-reconfigure wicd
2.update-rc.d wicd defaults

```
2. Then I've rebooted BackTrack again and the error was fixed.

---------------------------------------------------------------------------------------------------------------------
**After trying all those Tutorials, NONE of them actually helped me to find Wireless Networks.**

So now the question is... [B]How to get that WiFi working?
I will be really happy, if someone tell me how to update the firmware drivers (I think this is why it's not working)[/B]

---

### Post by QIII on 2013-12-02
*Moved to **Other OS/Distro Support***

---

### Post by adlerademov on 2013-12-02
Nice Picture, QIII !
SOLVED, this is the new statement of my problem, and I am really glad to tell it :)

[U]What I've done?
[/U]I realized that I have to have the drivers for my wireless card, just because EVERY SINGLE tutorial and friend of mine DIDN'T WORK, so this is how I've done it...

1. Copied the file "iwlwifi-2030-6.ucode" to File System --> /lib/firmware (You can get this file from [http://wireless.kernel.org/en/users/Drivers/iwlwifi#Download](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Download))
- I dont remember did I have to install it so anyway if it doesnt work type "*dpkg -i --force-all firmware-iwlwifi_0.40_all.deb*" in Terminal (You can get this file from [http://packages.debian.org/sid/all/firmware-iwlwifi/download](http://packages.debian.org/sid/all/firmware-iwlwifi/download)) (Keep in mind you have to copy it to /lib/firmware (I have it in the both folders))
2. Open terminal and type "modprode -r iwlagn" then "modprobe iwlagn" (without quotes)
3. Restart BackTrack 5 R3
4. Open terminal and type /etc/init.d/wicd start
5. Open Wicd and go to Properties. On the "Wireless Interface" i typed "wlan0" (without quotes) (I have "wlan0" typed too in "Wired Interface")
6. Click on Refresh button

THATS ALL, now I am going to put this thread prefix: SOLVED !

---

