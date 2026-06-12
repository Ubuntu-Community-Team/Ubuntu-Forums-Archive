---
title: "Wireless not connecting"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-07-02
I just finished installing my drivers with ndiswrapper and they worked great, I connected to the internet just fine, But right after I restarted I can't connect and I don't know why. My wireless is showing up and it says I'm sending and recieving packets, I'm also getting a signal strength at 80% while in roaming mode. Does anyone know why it's doing this but won't connect to the internet? Thanks.

---

### Post by Bofur on 2007-07-02
Please?

---

### Post by Bofur on 2007-07-03
justin@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:35:5B:24   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by smo0th on 2007-07-03
be sure you don't have duplicate DNS, check my previous post here:

[http://ubuntuforums.org/showthread.php?p=2472174#post2472174](http://ubuntuforums.org/showthread.php?p=2472174#post2472174)

---

### Post by Bofur on 2007-07-03
This is what my interface says if it means anything: 
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0
```

---

### Post by Bofur on 2007-07-03
When I go to network tools and click wlan0 it shows nothing, but when I plug in my ethernet cable it shows the ip address and everything.

---

### Post by Bofur on 2007-07-03
Someone has to have some idea? PLEASE??? I really need help!!!

---

### Post by GeeZor on 2007-07-03
ip settings?

Dont use DHCP, try setting your IP manually.. After that add you gateway like this
```
 
route add default gw <GATEWAY-IP>

```
also you could look here:
[http://www.cpqlinux.com/routes.html](http://www.cpqlinux.com/routes.html)

question. How do you set your profile for your wireless connection ???

---

### Post by Bofur on 2007-07-03
```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:5B:29:E0  
          inet addr:10.75.0.6  Bcast:10.75.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe5b:29e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:267886 (261.6 KiB)  TX bytes:38642 (37.7 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CF:B3:76:72  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1018 (1018.0 b)  TX bytes:168 (168.0 b)
          Interrupt:17 Memory:ecffc000-ed000000 

```

What is DHCP? And my IP is not static, so wouldn't I have to change it every time i restart?

---

### Post by GeeZor on 2007-07-03
DHCP is Dynamcally assigned IP adres control protocol, it provides you with an ip adress.
My experience is that that mechanisme sometimes doesn't work well. 
And you are connecting to you wireless router, the IP adress you need to communicate with your router is static so you shouldn't need to change that once it is set....

---

### Post by Bofur on 2007-07-03
Where do I get the gateway address?

---

### Post by GeeZor on 2007-07-03
that depends,
most of the time its 192.168.0.1
but you should post your ip configuration to be sure

---

### Post by smo0th on 2007-07-03
> **Bofur said:**
> This is what my interface says if it means anything: 
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto eth0
```

you don't have configured your wlan0 interface, take a look at my previous post and try using the code, instead of ra0 put wlan0 and fill your own parameters with your network information.

---

