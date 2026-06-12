---
title: "Detailed Network Problems"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by andrew.46 on 2006-12-30
Hi,

 I have been wrestling for about a week trying to connect my Xubuntu 6.06 computer via a DSL-502T router and have now reached head-banging stage. Can anybody have a look at the info below and tell me where I am going wrong? I am confident the computer can connect as it has intermittently worked and downloaded about 90 megs of updates, BlueFish html editor and open office writer.

 The computer is an Hp P3 e-PC with Ethernet card. The modem router is a D-Link DSL-502T. There is a known problem where the DNS servers are ot automatically picked up by DHCP and have to be put in manually. This is where I briefly managed to connect to the Internet. DHCP always changed these settings back to the incorrect ones (giving the DNS server as simply the IP address of the router) and the connection would die.

 I sought advice from my ISP and the makers of the router and setup a fixed IP connection rather than DHCP and this did not work at all. My final settings were:

IP Address: 10.1.1.10
Subnet Mask: 255.255.255.0
Gateway Address: 10.1.1.1
DNS Servers:

203.8.183.1
192.189.54.17
192.189.54.33

 I ran ifconfig but I cannot interpret the results which are as follows:

andrew@Troy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:02:07:CB:7F
          inet addr:10.1.1.10  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe07:cb7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:5928 (5.7 KiB)
          Interrupt:3 Base address:0xef80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5130 (5.0 KiB)  TX bytes:5130 (5.0 KiB)

I am persisting with this exasperating problem as the computer has successfully connected to the internet on at least 3 occasions and I am sure that there is a setting that I have stuffed up.

 I would be very grateful to anybody who can guide me in this matter,

                             Andrew

---

### Post by teaker1s on 2006-12-30
[http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034")

---

### Post by andrew.46 on 2006-12-30
Hi,

 Thanks for your prompt reply:

> **teaker1s said:**
> [http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034")

 I followed these instructions to the letter but unfortunately no result; so I reversed the steps.

 Can I say from my frustration that Windows XP and Windows 2000 found this router and its settings and had it up and running in less than 5 minutes. I have been trying to get Xubuntu to do the same for at least 2 hours every day for a week. Hmmmmm....... I am trying to be a believer......

                          Andrew

---

### Post by Jussi01 on 2006-12-30
Hi andrew.46,

Unfortunately I dont have help for your problem - but I just wanted to say keep persisting - **when** you do get it sorted it will feel so good :)

---

### Post by PilotJLR on 2006-12-30
try adding this to the beginning of your /etc/resolv.conf
```

nameserver 203.8.183.1
nameserver 192.189.54.17
nameserver 192.189.54.33

```

And then do this:
```

sudo /etc/init.d/networking restart

```

---

### Post by fana2 on 2006-12-30
Can you ping your Gateway ?

---

### Post by andrew.46 on 2006-12-30
Hi,

 Thanks for replying:

> **fana2 said:**
> Can you ping your Gateway ?

Not from the Linux computer (I could not find the program: default install of Xubuntu 6.06 does not seem to have the nice 'Network Tools' section), as I cannot even raise the router but I have been able to ping this from the windows computer.

                   Andrew

---

### Post by fana2 on 2006-12-30
Open a Terminal Window

```
ping 10.1.1.1
```

---

### Post by andrew.46 on 2007-01-03
Hi,

 Well, I actually took the computer to work and booted it into the LAN there and guess what?? Xubuntu picked up the network perfectly and was online immediately.

 I think I was a little too quick to blame Xubuntu and I now believe that the prime culprit is in fact the DSL-502T router which I am in the process of replacing.

 I am buying a SpeedStep 585 which has a 4 port ethernet switch: 1 to the Windows box and 1 to Xubuntu: should work a little more easily I hope :) :) 

                        Andrew

---

