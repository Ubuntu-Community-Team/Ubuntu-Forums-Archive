---
title: "Wireless Blues"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2007-01-13
WUSB54G Ver4
Ubuntu CE EDGY

Trying to get remote PC connected to internet.

Is the command: foo@bar: ~& if config a legitimate line or is "&" actually "$" I cannot see well enough to read the font.

From Network setting I see my wireless card and the ESSID is clemkonan and the address is DHCP. Checking my card I get:

vincyman1@vincyman1-desktop:~$ foo@bar: ~$ ifconfig
bash: foo@bar:: command not found
vincyman1@vincyman1-desktop:~$ foo@bar:~& ifconfig
[1] 8354
bash: foo@bar:~: command not found
eth0      Link encap:Ethernet  HWaddr 00:E0:06:FA:6F:21  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:6ff:fefa:6f21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2292999 (2.1 MiB)  TX bytes:292061 (285.2 KiB)
          Interrupt:5 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3289035 (3.1 MiB)  TX bytes:3289035 (3.1 MiB)

rausb0    Link encap:Ethernet  HWaddr 00:16:B6:94:A9:CD  
          inet6 addr: fe80::216:b6ff:fe94:a9cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55844 (54.5 KiB)  TX bytes:146580 (143.1 KiB)

[1]+  Exit 127                foo@bar:~
vincyman1@vincyman1-desktop:~$ 

What does all this mean and is my driver already present in this release I have also down loaded rt2500-1.1.0-b4.tar but  i do not know where to go from there.
Thanks

---

### Post by Pobega on 2007-01-13
This thread here should probably work for Ubuntu 6.10 Edgy, I'd be surprised if it didn't. 

[http://ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G](http://ubuntuforums.org/showthread.php?t=192588&highlight=WUSB54G)

---

### Post by jpeddicord on 2007-01-13
Whenever someone posts foo@bar:~$ or similar, ignore it. Do not type it in. It is only to show what the terminal looks like when typing.

So, if someone tells you to type:
```
foo@bar:~$ ifconfig
```just type **ifconfig** to run the command. Everything before the $ is for display purposes only.

That might help in solving your problem. :)

---

### Post by Pobega on 2007-01-13
> **jacobmp92 said:**
> Whenever someone posts foo@bar:~$ or similar, ignore it. Do not type it in. It is only to show what the terminal looks like when typing.

So, if someone tells you to type:
```
foo@bar:~$ ifconfig
```just type **ifconfig** to run the command. Everything before the $ is for display purposes only.

That might help in solving your problem. :)

Yes, that too. Usually anything before a $ or # in a command is for show only, $ is for user and # is for root. Just ignore it and type in the command.

> root@comp:~# ifconfigJust type:> ifconfig

---

### Post by clemkonan on 2007-01-13
Thanks for the info I will press on

---

### Post by clemkonan on 2007-01-13
Sorry but I am trying to do the set up using RT2500 RALINK DRIVER WHICH MEANS I do not need NDiswrapper.

Maybe there is a post specific to the Ralink 2500 or 2700 

Thanks

---

### Post by clemkonan on 2007-01-13
If I am trying to install the driver package for rt2500-1.1.0b4 does the line

sudo apt-get install buil-essential linux-headers- 'uname -r' gcc-3.4

mean that 'uname -r' is changed to rt2500-1.1.0-b4?

Thanks
Source Ralink RT2570 usb wireless driver from Ubuntu doc storage facility

---

