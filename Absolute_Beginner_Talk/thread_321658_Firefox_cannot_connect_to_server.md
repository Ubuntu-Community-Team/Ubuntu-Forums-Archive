---
title: "Firefox cannot connect to server"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by wmecity2729 on 2006-12-19
Hi, I just install Ubuntu 6.10(dual boot with XP).
On ADSL setup, I already run terminal "pppoeconfig" and set username and
password.

On Firefox change IP6 address to false. But still firefox cannot connect to server(internet).

a. Network card is Realtek model RTL8139
b. ADSL bridge/router is ZTE model ZXDSL 831
 
Please help.:)

---

### Post by taurus on 2006-12-19
What's the output of this command?

```
ifconfig
```
Did the LiveCD find your network at all?  Can you surf the net from the LiveCD?

---

### Post by wmecity2729 on 2006-12-19
Hi, sorry for late reply. Below is the ifconfig result.

eth0   Link encap: Ethernet HWaddr 00:13:8F:93:B0:F7
         inet addr: 192.168.1.2   Bcast: 192.168.1.255   Mask: 255.255.255.0
         inet6 addr: fe80:213:8fff:fe93:bof7164   Scope: Link
         UP BROADCAST RUNNING MULTICAST MTU: 1500   Metric: 1
         RX packets: 101   errors: 0   dropped: 0   overruns: 0   frame: 0
         TX packets: 182   errors: 0   dropped: 0   overruns: 0   carrier: 0
         collisions: 0   txqueuelen: 1000
         RX bytes: 6402 (6.2 KiB)   TX bytes: 16345 (15.9 KiB)
         Interrupt: 209   Base address: 0xcc00

lo       Link encap: Local Looback
          inet addr: 127.0.0.1   Mask: 255.0.0.0     
          inet6 addr:  ::1/28   Scope: Host
          UP LOOPBACK RUNNING MTU: 16436   Metric: 1
          RX packets: 68   errors: 0   dropped: 0   overruns: 0   frame: 0
          TX packets: 68   errors: 0   dropped: 0   overruns: 0   carrier: 0
          collisions: 0   txqueuelen: 0
          RX bytes: 5348 (5.2 KiB)   TX bytes: 5348 (5.2 KiB) :)

---

### Post by chadk on 2006-12-19
Looks like you're connecting OK as you have RX and TX bytes.  How about if you ping yahoo.com or something?  Does it ping or do you get an "unreachable error"?

---

### Post by peggyjo on 2006-12-20
I'm having a similar problem with newly installed Ubuntu 6.06 dual boot on a Windows XP machine. I have the same modem.

Sporadically I will be able to connect to the Internet, then connection becomes very very slow, then I'm unable to connect at all. 

I have the same card mentioned above -- Realtek RTL8139.

Everything connects just fine when I'm booted up in Windows.

I did try pinging yahoo.com, as suggested, and got quick results. Also tried pinging some of the sites I could not connect to, and those worked fine as well.

Any ideas of what could be causing this?

---

### Post by wmecity2729 on 2006-12-21
Hi, sorry for not reply.
However, now I manage to surf internet using Ubuntu.
I do not how though. I just reinstall back the whole thing 
and it works, just like that.
I guess we need to be patient and it will pay off.

Thanks for all help, reply and sharing.

:)

---

### Post by Erenlinux on 2007-01-05
ifconfig eth0 ip adress up

or eth1 , eth2 ....

example : ifconfig eth0 192.168.0.1 up

:)

---

