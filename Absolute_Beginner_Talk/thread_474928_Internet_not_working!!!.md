---
title: "Internet not working!!!"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-06-15
Hi, 

Internet is not workin in ubuntu but in firefox after disabling ipv6.. I can browse now. But other than that, no internet connection exists. I can't do "sudo apt-get install". Can anyone help me out?

Thanks!!!

---

### Post by meborc on 2007-06-15
so you have internet in the browser, but not while using apt?

what is the output when you try to do "sudo apt-get update"?

can you post the output of "ifconfig"!

---

### Post by icyblue on 2007-06-15
**when I use the command "sudo apt-get update"**

It stops around 37% [connecting to in.archive.ubuntu.com(1.0.0.0)]

**Here is the output of "ifconfig"**

eth0      Link encap:Ethernet  HWaddr 00:80:48:42:97:E2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4175126 (3.9 MiB)  TX bytes:777499 (759.2 KiB)
          Interrupt:177 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by meborc on 2007-06-15
if you have internet in the browser, then you are connected... the problem could be in the servers where you are trying to update... you could try removing the in. (the country code) from before the server name

for example in stead of **in.archive.ubuntu.com** just **archive.ubuntu.com**
```

sudo gedit /etc/apt/sources.list
```
to change the servers... then ```
sudo apt-get update
```now your computer tries to connect to the main ubuntu repositories instead of your country ones...

report back if something still fails

---

### Post by icyblue on 2007-06-15
I changed in.archive.ubuntu to archive.ubuntu.... Nothing happened. It stopped at the same 37%. Also, not jus the "sudo" things but also gaim not workin and the whole internet does not work except for the browser.. it appears like this now

37% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.co

---

### Post by meborc on 2007-06-15
and it was working fine before disabling ipv6? have you tried to enable it again just to see if this is the problem (although i highly doubt it)

sorry... never encountered this kind of problem before, can't help much :)

---

### Post by icyblue on 2007-06-15
Actually, nothing worked before disabling ipv6. After disabling it, browser worked. Forgot to mention, I disabled ipv6 only in the browser and not in resolv.conf..... I tried it though, but it didn't work too...

---

### Post by meborc on 2007-06-15
i have no more ideas... maybe someone else can help...

---

### Post by icyblue on 2007-06-16
Anyone else can help me??

---

### Post by Outrunner on 2007-06-16
Just wondering, what happens when you type
```

ping -c 5 bbc.co.uk
```

---

