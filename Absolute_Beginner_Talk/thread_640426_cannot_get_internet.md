---
title: "cannot get internet"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by vikraman on 2007-12-14
Hi, 

I am a new user and this is my first time at linux, I've installed Ubuntu Feisty Fawn just a week ago. I am using smartAX MT 882 ADSL broadband modem using USB cable and I am getting vey good internet connectivity in winxp installed in another partition. But in ubuntu although the USB driver was installed I am not getting the internet connection. 
The normal configuration of the USB modem in winxp is ip address 192.168.1.10 netmask 255.255.255.0 gateway is 192.168.1.1 and DNS is 192.168.1.1. After that the user name and password will be configured by opening [http://192.168.1.1](http://192.168.1.1). But I cannot open [http://192.168.1.1](http://192.168.1.1) in ubuntu.
the ifconfig eth0 in ubuntu is 
> eth0      Link encap:Ethernet  HWaddr 00:0F:A3:50:E0:40
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask: 
         255.255.255.0
          inet6 addr: fe80::20f:a3ff:fe50:e040/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:32 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) I dont know how to solve this. kindly help me

---

### Post by bigken on 2007-12-14
could be ipv6 in the browers type about:config then in the search filter type ipv6 just double click the result to change from true to false 

if your modem has user name and password already set  you should just be able to plug and play a better option is a adsl/modem/router ie netgear

---

### Post by 3rdalbum on 2007-12-14
You say that you're using the broadband modem "through USB cable". Does that mean that the modem has an Ethernet port in it? (it looks like a big phone line port).

If it has an Ethernet port in it, and your computer has the same port, dude, use that! It will give you better performance than through USB, and will probably set itself up on Linux. If you don't have an Ethernet cable lying around, go to your local electronics shop and ask for a "Cat 5 cable".

---

### Post by vikraman on 2007-12-15
Hi,
Although I am having an ethernet card whic is a RTL-8139D and works fine on Windows XP, but it is detected in Ubuntu. Since the driver for this card is not availble it shows not eth0 connection.I used ipconfig, ipconfig eth0, lspci and lspci -n in the console and the result is
> v@v-desktop:~$ ifconfig
lo Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1 RX packets:2 errors:0 dropped:0 overruns:0 frame:0 TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)
> v@v-desktop:~$ ifconfig eth0
eth0: error fetching interface information: Device not found
> v@v-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:0a.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)
> v@v-desktop:~$ lspci -n
00:00.0 0600: 8086:7120 (rev 03)
00:01.0 0300: 8086:7121 (rev 03)
00:1e.0 0604: 8086:2418 (rev 02)
00:1f.0 0601: 8086:2410 (rev 02)
00:1f.1 0101: 8086:2411 (rev 02)
00:1f.2 0c03: 8086:2412 (rev 02)
00:1f.5 0401: 8086:2415 (rev 02)
01:0a.0 0200: 1904:8139 (rev 01)
That is why I am trying to use USB cable. I am using smartAX MT 882 ADSL broadband modem using USB cable and I am getting vey good internet connectivity in winxp installed in another partition. But in ubuntu although the USB driver was installed I am not getting the internet connection. 
The normal configuration of the USB modem in winxp is ip address 192.168.1.10 netmask 255.255.255.0 gateway is 192.168.1.1 and DNS is 192.168.1.1. After that the user name and password will be configured by opening [http://192.168.1.1](http://192.168.1.1). But I cannot open [http://192.168.1.1](http://192.168.1.1) in ubuntu.
the ifconfig eth0 in ubuntu is 
> eth0 Link encap:Ethernet HWaddr 00:0F:A3:50:E0:40
inet addr:192.168.1.10 Bcast:192.168.1.255 Mask: 
255.255.255.0
inet6 addr: fe80::20f:a3ff:fe50:e040/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:32 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 
how to correctly configure the network interface so that I can get internet. what is broadcast address? what is matric? kindly guide me

---

### Post by fourscore on 2007-12-16
There is an issue with Realtek Ethernet card when dual booting with Windows and Linux. Pls refer to the flwg link - [http://ubuntuforums.org/showthread.php?p=3446114](http://ubuntuforums.org/showthread.php?p=3446114)

---

### Post by vikraman on 2007-12-23
Hi, the problem solved. I changed the LAN card and now I am able to get internet. but one problem in ubuntu 7.04, the firefox does not open web pages. it shows 'server not found'error. so I installed kubuntu where the konqurer is diplaying web pages correctly. thanks to all

---

