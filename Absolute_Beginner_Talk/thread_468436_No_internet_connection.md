---
title: "No internet connection"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by chichigarland on 2007-06-08
I installed the Ubuntu 7.04 desktop edition on my dell precision 420. Everything went well during the installation.  After reboot, I used system--> admin--> network to set up the wired connection with a static IP address. However, I could not get the internet connection. 

output of  lspci:

...
02:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
...


output of ifconfig:

eth0              Link encap: Ethernet   HWaddr   00:B0:7B:E3:9D
                     inet addr: 128.138.189.125    Bcast: 128.138.189.255     Mask:255.255.255.0
                     inet6 addr: fe80::2b0:d0ff:fe7b:e39d/64   Scope: Link
                     UP BROADCAST RUNNING MULTICAST    MTU: 1500      Metric 1
                     RX packets: 24    errors: 0    dropped: 0 overruns: 1  frame: 0
                     TX packets: 20    errors: 0    dropped: 0 overruns: 0   carrier: 14
                     collisions: 0    txqueuelen:  1000
                     RX bytes: 2501 (2.4  KiB)   TX bytes: 1416 (1.3 KiB)
                     Interrupt: 17    Base address: 0x2c00

lo                  Link encap: Local Loopback
                    inet addr: 127.0.0.1          Mask: 255.0.0.0
                    inet6 addr:  ::1/128    Scope: Host
                    UP LOOPBACK RUNNING   MTU: 16436     Metric: 1
                    RX packets: 135    errors: 0    dropped: 0 overruns: 0  frame: 0
                     TX packets: 135    errors: 0    dropped: 0 overruns: 0   carrier: 0
                     collisions: 0    txqueuelen:  0
                     RX bytes: 12851 (12.5  KiB)   TX bytes: 12851 (12.5 KiB)


How can I fix the problem?

Thanks a lot!!

---

### Post by Seisen on 2007-06-08
Are you runnning directly from the cable modem or from a router.

---

