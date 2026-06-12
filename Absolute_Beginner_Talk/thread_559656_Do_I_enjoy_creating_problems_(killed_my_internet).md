---
title: "Do I enjoy creating problems? (killed my internet)"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by weezerisrock on 2007-09-25
Ok, I had ubuntu loaded on my computer, and then I decided to load windows up too for a couple of games.  I learned how to install windows and fix the grub afterward which I did successfully.  However coming back to ubuntu I noticed that my network card is dead in the water.  No lights on the network card, no lights on my router.

It does work in windows.  I can mark it stopping working from the first boot after getting windows and the grub up and running.  :confused:  So I need your guys' brilliant help.  What information do you guys need me to post tonite from my computer to help you diagnose my system?

Thank you for your upcoming help!

Here is my current IFCONFIG. 

```
eth0      Link encap:Ethernet  HWaddr 00:01:80:3F:B9:6E  
          inet6 addr: fe80::201:80ff:fe3f:b96e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth0:avah Link encap:Ethernet  HWaddr 00:01:80:3F:B9:6E  
          inet addr:169.254.6.201  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2493 (2.4 KiB)  TX bytes:2493 (2.4 KiB)
```

---

### Post by upbeat.linux on 2007-09-25
1. what kind of router are you using and what address range is it supposed to assign to you? 

2. do you have an address reservation on your router for the specific mac address?

3. what does: ```
cat /etc/network/interfaces
``` return?

4. do you have firestarter configured?

---

### Post by weezerisrock on 2007-09-25
1. address range is 192.168.1.1xx-254

2. no reservations except wireless. (only applicable to laptop which is working fine.)

3. ```
 cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

4. no.  I'm not sure what you are reffering to when you say firestarter.

Thanks for the response!

---

### Post by weezerisrock on 2007-09-27
anyone have any suggestions?  Or should I just reload?

---

### Post by upbeat.linux on 2007-10-04
sorry for not getting back to you sooner...anyways, it looks like there might be an error in the interfaces file.

the line:

```
iface eth0 inet dhcp
```

should have

```
auto eth0
```

preceding it. You'll then need to restart network services.

Should look like this:

```
auto eth0
iface eth0 inet dhcp
```

---

### Post by weezerisrock on 2007-10-04
oooo thank you, I was gonna reload this weekend.  I'll try this tonite.

---

### Post by weezerisrock on 2007-10-05
Didn't get a chance to try this last night, I'll try it today.

---

