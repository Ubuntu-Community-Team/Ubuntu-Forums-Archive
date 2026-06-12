---
title: "I tried to search, synaptic, apt, it dont work"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by DemonKnightDK on 2007-07-08
okay, I can get on the internet, I can network print, but for the life of me, synaptic, and apt will not download updates or or any thing. I can open and run them, select what I want and will not down load. 

I've recently installed a belkin router, which as I said every thing else works fine..

Any ideas?

---

### Post by taurus on 2007-07-08
What's the output of this command from a terminal?

```
ping -c 3 www.google.com
```
Or

```
/sbin/ifconfig
```

---

### Post by DemonKnightDK on 2007-07-08
david@david-desktop:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:5B:AE:8C:BA  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:feae:8cba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1659539 (1.5 MiB)  TX bytes:395385 (386.1 KiB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2291 (2.2 KiB)  TX bytes:2291 (2.2 KiB)

david@david-desktop:~$ ping -c 3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=245 time=28.3 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=245 time=27.9 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=3 ttl=245 time=28.5 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10107ms
rtt min/avg/max/mdev = 27.995/28.275/28.527/0.292 ms

I'm runing ubuntu 7.4 if that matters.

---

### Post by forrestcupp on 2007-07-08
Do you have the Synaptic update program running in the background?  If so, that could keep another instance of apt from installing things.

---

### Post by DemonKnightDK on 2007-07-08
Its all working fine now. Not sure exactly why but I aint complaining.

---

### Post by Hairy_Palms on 2007-09-26
k ive got this exact same problem, does anyone have any ideas on how to solve?

---

### Post by jw5801 on 2007-09-26
Can you give some more info on the problem? What happens when you try to run it? Does it give an error message, if so post it here.

---

### Post by Hairy_Palms on 2007-09-26
i recently moved in to a shared house, where i connect via wireless with WPA,
i can browse the internet and use bittorrent fine, but thunderbird wont get emails, pidgin wont connect, and synaptic wont do anything. does anyone know what the problem is? on windows MSN messenger and thunderbird both work.
no error messages other than the synaptic ones saying couldnt connect to archive.ubuntu.com etc.

---

### Post by jw5801 on 2007-09-26
Hmm... can you ping archive.ubuntu.com? or anywhere else from the commandline for that matter?

---

### Post by Hairy_Palms on 2007-09-26
its ok, i found the solution in this thread, it was a DNS issue with the shitty zoom router thats being used [http://ubuntuforums.org/showthread.php?t=282034&page=4](http://ubuntuforums.org/showthread.php?t=282034&page=4)

---

