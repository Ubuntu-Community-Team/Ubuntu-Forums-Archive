---
title: "Network Problems"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by tibbar110 on 2006-07-21
I am hoping somebody can help me.  I am fairly adept with computers, and have an Ubuntu partition on a PC, but cannot get the network functioning.  

My partitions are the following with System Commander 7:
(0,0) - Windows 2000
(0,1) - Windows 98se
(0,2) - Windows XP Pro
(0,3) - Extended (Linux - Ext2 & Swap)

I have DHCP functioning for all three Windows partitions, and it appears that it works for Linux as well.  (6.06)  Unfortunately, it is not pingable on my other machines nor can it ping any of them.  I tried creating a static IP in the same network, but it did not work either.  

Any ideas?

---

### Post by scxtt on 2006-07-21
what's the output of **ifconfig -a**?

---

### Post by tibbar110 on 2006-07-22
How do I copy and past that output?  I have no access to the network or my other partitions.

---

### Post by scxtt on 2006-07-22
well, do you have entries for eth0 or eth1, etc. something like:

```
:> ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D4:CB:7E:54
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fecb:7e54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:52588498 (50.1 MiB)  TX bytes:2806865 (2.6 MiB)
          Interrupt:225 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:644 (644.0 b)  TX bytes:644 (644.0 b)
```

---

### Post by tibbar110 on 2006-07-22
That looks very much like what I have.  The network is slightly different.  192.168.0.0.  Does that help at all?

If I can manage to mount my NTFS partitions in Linux, I can do a complete copy and paste.

---

### Post by richbarna on 2006-07-22
You need to boot into linux and perform the command from the terminal.
Then write down the >  inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0 part.

Are you using a hub or are you connecting directly to a router?

Also, check your firewall settings that ping and echo request is allowed.

---

