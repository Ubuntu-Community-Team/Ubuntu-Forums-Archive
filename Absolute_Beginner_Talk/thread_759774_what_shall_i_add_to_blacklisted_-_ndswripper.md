---
title: "what shall i add to blacklisted - ndswripper"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Walc on 2008-04-19
welcome
im experiencing some issues with getting my laptop intel PRO/Wireless wireless card to work on my ubuntu 7.10. Network manager doesnt detect wireless network <i have linksys wrt54gs plugged to desktop with vista onboard>.All i can see is wired and modem network, both inactive.
Cuz of the above i was adviced to install windows driver via ndswripper.
I have found a tutorial, but already encountered problems / 

1. when adding *inf driver via windows wireless drivers, it says : invalid driver

2. im thinking this might be caused by the fact that i havent blackilsted old driver yet <but in that tutorial this should be step 3, not step 2>...now the big question is how do i know whats the exact name of the driver that needes to be added to blacklisted?

<this tutorial that i mentioned above is done on an atheros communications wireless card, so he added ath_pci, what shall i add?>

thx in advance

---

### Post by Walc on 2008-04-19
any1?>

---

### Post by annda on 2008-04-19
first of all, which Intel chip do you have? most should work with restricted kernel modules, but i understand yours doesn't.

what does the output of this command say?

```
sudo lshw -C network
```

---

### Post by Walc on 2008-04-19
```

robert@lapek:~$ sudo lshw -C network
[sudo] password for robert:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:17:08:2d:bb:a3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.1.102 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
robert@lapek:~$ 

```


intel PRO/Wireless 3945abg

---

### Post by LarryJ2 on 2008-04-19
I have a working Intel 3945wireless chips in two  Dell laptops. A very frustrating experience with all wireless network managers until I tried  wicd.  Now it works flawlessly with my Buffalo WHR-G54B router and Intel 3945AGB.

Info here:  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Instructions for installing in Ubuntu are here:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Larry

---

### Post by annda on 2008-04-19
the driver for your wireless  is part of the kernel and it should be working

if you get output from this command, the driver is loaded:
```
lsmod | grep 3945
```

some laptops have problems with the wifi on/off switch. do you have one? it the wifi led on?

check this guide for more  troubleshooting:
[https://help.ubuntu.com/7.10/internet/C/wireless.html](https://help.ubuntu.com/7.10/internet/C/wireless.html)

and of course post back with any problems or questions

---

### Post by Walc on 2008-04-19
@Annda:

```

robert@lapek:~$ lsmod | grep 3945
ipw3945               119840  1 
ieee80211              35656  1 ipw3945
robert@lapek:~$ 



```

wifi switch is on <blue led is lit>
it turns on bluetooth as well <which i can see cuz of the blue icon, but still cant see wireless network in network manager

my laptop is connected via ethernet atm, so i can check back online, is that a problem? i mean shall i unplugg it and try only with wifi?

---

### Post by annda on 2008-04-19
let's test you wireless completely: unplug the cable, quickly disable the ethernet interface

```
sudo ifdown eth0
```

and now check wifi connectivity. reboot if necessary (no cable)

---

### Post by Walc on 2008-04-19
```

robert@lapek:~$ sudo ifdown eth0
[sudo] password for robert:
ifdown: interface eth0 not configured
robert@lapek:~$ 








```

restarted and no wireless network found <usinf wincd this time>

---

### Post by annda on 2008-04-19
sorry to hear that. i'm running out of ideas but let's check the wireless interface. what does 

```
ifconfig
```

say?

---

### Post by Walc on 2008-04-19
```

robert@lapek:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:08:2D:BB:A3  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe2d:bba3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3402403 (3.2 MB)  TX bytes:465772 (454.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

robert@lapek:~$ 


```

---

### Post by annda on 2008-04-19
i don't know what causes this, but your wireless is definitely NOT enabled. 

try this to poll the state of the switch:

```
dmesg | grep Radio
```

by the way, are you dual-booting or is it a pure Ubuntu laptop? on an old laptop i've had problems switching wifi on with Ubuntu after is was switched off in Windows...

---

### Post by Walc on 2008-04-19
```

robert@lapek:~$ dmesg | grep Radio
[   17.076000] ipw3945: Radio Frequency Kill Switch is On:
robert@lapek:~$ 

```

its ubuntu only
but used 2 be xp b4
and im afraid it might have been turned off then.....

---

### Post by annda on 2008-04-19
can you switch in on using the keyboard? if so, try this and check the output of ifconfig. a new interface (probably eth1 or wlan0) should appear.

or is a button/slider? in this case, your BIOS should have a wireless option somewhere that you can change from 'remember last state' to 'always on' or something like that. this should help.

---

### Post by Walc on 2008-04-19
well its a button
checked bios and there was wlan/lan switching which i enabled....i guess it was that tho
theres no such option u r reffering to

---

