---
title: "Live CD + Internet problems"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by ljk on 2006-09-06
I would like to convert to Open Source Software and wanted to try Linux. I downloaded Ubuntu and opted for the "Live CD" to see what it was like. It seems great apart from the problem of connecting to the internet.

I have a static IP address & a hard-wired ethernet connection. This has worked fine on both Windows XP & Mac OS 10.4

All my attempts at entering the address/router or gateway etc. information in the Network panels have failed to get an internet connection up and running. In the "Hosts" panel I selected "All".

Is the "Live CD" incapable of setting-up such a connection?

What information is *essential *versus *optional*?

Many thanks to anyone who might help me resolve this problem.

---

### Post by Eproxus on 2006-09-06
Try running:
```
sudo ifconfig
```
And find your network interface. When you know which one it is you can run:
```
sudo ifconfig *[interface]* up
```
Where *[interface]* is your interface. After that try:
```
sudo ifconfig *[interface]* *[static-ip]*
```
This will set the ip of the interface. Does this work?

---

### Post by ljk on 2006-09-07
Many thanks.

Will try this next week when I go back to work & post the result here.

As I am an absolute beginner at this "run code" stuff, do I need to open any applicaton to run the code in?

Is there any "point - click - type the info in the boxes" method of achieving the same ends?

Greatly obliged & best regards.

---

### Post by Eproxus on 2006-09-07
Sorry! That I should have thought of!

All commands should be run in a terminal. To access the terminal go Applications -> Accessories -> Terminal. See [this guide]("http://linux.org.mt/article/terminal") for more information.

Regarding "point-click" I assumed that's what you already tried. I've had some bad experience with those tools before (they may work now). There is also the possibility of installing another graphical network tool, such as Network Manager.

Also, when running ifconfig the output looks like this for me:
```
ath0      Link encap:Ethernet  HWaddr 00:02:E3:47:5D:4A
          inet addr:192.168.1.32  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe47:5d4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134680 errors:139821 dropped:0 overruns:0 frame:139821
          TX packets:110368 errors:136 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:112481880 (107.2 MiB)  TX bytes:10670318 (10.1 MiB)
          Interrupt:185 Memory:f8a60000-f8a70000

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:AC:7A:77
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:461 (461.0 b)  TX bytes:461 (461.0 b)

```

I have two network devices and a loopback device. If you have more than two devices (except the loopback) you need to know which one is your wired one and use it to set the IP.

---

### Post by ljk on 2006-09-08
Again, my sincere thanks.

The intended ubuntu box is at work (a school)and I won't be able to try anything out until next week at the earliest. I will post a message letting you know the outcome.

Best regards.

---

### Post by ljk on 2006-10-25
Apologies for the time this has taken. The machine I intended to use has had some problems & my efforts to convert it to a small server for some small classes will, apparently, not work anyway.
The IP address begins with 192.168. etc. which, I now learn, is a block of addresses reserved for internal use only.
I will persevere with getting an Ubuntu system (internet capable) up & running and offer my thanks for the invaluable help you so kindly gave.

Many thanks indeed.

---

### Post by Eproxus on 2006-10-25
If you're connected to a router (possibly also a broadband modem) that's probably a correct IP-number.

---

### Post by ljk on 2006-11-02
Thanks again. I've managed to get an intel based laptop (wired) to run Ubuntu AND connect to the internet from the live cd by noting and entering the info about IP address /gateway /DNS server etc which I had no idea how to obtain before getting help from your goodself.
I hope to do a backup of the hard disk and then a permananent (dual boot) installation of Ubuntu.  Best regards.

---

