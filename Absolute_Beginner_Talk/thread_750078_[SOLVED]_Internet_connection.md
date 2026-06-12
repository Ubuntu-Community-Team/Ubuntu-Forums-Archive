---
title: "[SOLVED] Internet connection"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-04-09
Hi all,

I have installed Kubuntu in one of my sytem. But I am not able to configure net connection.

Actually I have successfully installed net connection in my Ubuntu OS in my other system.

I have Broadband net connection.

My modem is beetel 220BXI ADSL2 + Modem.

I have tried and successfully configured "sudo pppoeconf"

Eventhough, in Kubuntu when i run the following line in "konsole" it throws some errors

"PAP Authentication failed" "Connection denied"

Can anybody help me to solve this problem?

Regards,
Srikrishnan

---

### Post by Crafty Kisses on 2008-04-09
Post the following output:
```
ifconfig
```

---

### Post by srikrishnan on 2008-04-09
Hi,

This is the OUTPUT:

srikrishnan@srihari:~$ plog
Apr  9 20:49:26 srihari pppd[5455]: Plugin rp-pppoe.so loaded.
Apr  9 20:49:26 srihari pppd[5457]: pppd 2.4.4 started by srikrishnan, uid 1000
Apr  9 20:49:26 srihari pppd[5457]: PPP session is 4410
Apr  9 20:49:26 srihari pppd[5457]: Using interface ppp0
Apr  9 20:49:26 srihari pppd[5457]: Connect: ppp0 <--> eth1
Apr  9 20:49:26 srihari pppd[5457]: Remote message: permission denied
Apr  9 20:49:26 srihari pppd[5457]: PAP authentication failed
Apr  9 20:49:26 srihari pppd[5457]: Connection terminated.
srikrishnan@srihari:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:80:48:51:00:D0
          inet6 addr: fe80::280:48ff:fe51:d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:720 (720.0 b)  TX bytes:468 (468.0 b)
          Interrupt:11 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:08:5C:7F:E6:8E
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:5cff:fe7f:e68e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7802 (7.6 KB)  TX bytes:9955 (9.7 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Can you please help me?

Thanks in Advance,
Srikrishnan

---

### Post by srikrishnan on 2008-04-10
Hi All,

Please can anybody help me to solve this problem?

Regards,
Srikrishnan

---

### Post by mrdosa on 2008-04-10
Are you sure you entered, the right ID and Password at the time of the setup!? Check that once!

---

### Post by superprash2003 on 2008-04-10
if you want two pcs to use the internet simulatenously at one time, then you cannot use the dialing mode(ppoeconf mode), you need to make your modem to dial the connection.

---

### Post by srikrishnan on 2008-04-12
Hi, 

No at one time I am going to use one internet connection only.

Also, after my several attempts of trying to connect, surprisingly at last I succeeded without knowing what has been gone wrong at the first times.

Anyway thanks for your response

Regards,
Srikrishnan

---

