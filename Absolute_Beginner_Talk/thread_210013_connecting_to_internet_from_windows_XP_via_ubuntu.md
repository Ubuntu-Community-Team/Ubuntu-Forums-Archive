---
title: "connecting to internet from windows XP via ubuntu"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by lee45 on 2006-07-06
I have a ubuntu computer connected to the i nternet, by way of pppoeconf.
that is the ONLY way i have been able to connect to the internet
I also have an XP box that is connected via ethernet lan cable to this computer, which wishes to access the internet via the OTHER ethernet lan cable, which leads to a DSL modem.
I have followed directions elsewhere in these forums and got so far as to ping the XP from the linux machine, but that's it, no file sharing, no internet for the XP computer
I'm deeply suspicious that it's something to do with the pppoeconf connection, because when i do as recommended and change to a static ip, the connection fails and i'm offline
if anyone can get my XP box online, i don't even care if i can file share, tho that would be good too.

---

### Post by KrisDwyer on 2006-07-06
Hey Mate,

Have you set up the Ubuntu box as your default gateway?

---

### Post by lee45 on 2006-07-06
i don't think so, because my IP is dynamic, so i don't know what to enter in the gateway dialogue.
I've put in two DNS ips that i got from the terminal nameserv, but nothing in the gateway, not knowing what to put.

---

### Post by Apple 101 on 2006-07-06
On the Ubuntu computer use Synaptic to get Firestarter.  Use it to configure ICS for the system.

---

### Post by lee45 on 2006-07-06
[QUOTE=Apple 101]On the Ubuntu computer use Synaptic to get Firestarter.  Use it to configure ICS for the system.[/QUOTE]

i tried that, but firestarter says my ethernet is not working and cannot start.
also, i just noticed i have an X icon next to my volume control which tells me i have no active connections, when in fact, i have two, according to the networking section. (etho to internet,eth1 to XP computer.
i uninstalled firestarter, since repeated attempts could not get it to work.

---

### Post by dmizer on 2006-07-06
do you have a router between your ubuntu computer and your windows xp computer, or is there just a cable running from one to the other?

if there is no router, you will need to make sure that you are using a crossover cable which is different than a regular lan cable.

---

### Post by lee45 on 2006-07-06
[QUOTE=dmizer]do you have a router between your ubuntu computer and your windows xp computer, or is there just a cable running from one to the other?

if there is no router, you will need to make sure that you are using a crossover cable which is different than a regular lan cable.[/QUOTE]

no router, lan cable from dsl modem to eth0, then crossover cable from ethernet (eth1) card to xp computer. We used to be able to get the xp online with windows on this machine, but never really knew how, it didn't show any file sharing or anything.

---

### Post by dmizer on 2006-07-06
humm ... what is the output of ifconfig?

also ... have you tried a different crossover cable?  it could be that the cable is bad.

---

### Post by lee45 on 2006-07-06
[QUOTE=dmizer]humm ... what is the output of ifconfig?

also ... have you tried a different crossover cable?  it could be that the cable is bad.[/QUOTE]

here is what the terminal said to ifconfig, i hope it tells you more than it tells me : )

lee@lee-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:BA:8F:6D:0F
          inet6 addr: fe80::250:baff:fe8f:6d0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47983 errors:1 dropped:0 overruns:0 frame:0
          TX packets:39892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:128 txqueuelen:1000
          RX bytes:47713162 (45.5 MiB)  TX bytes:5622387 (5.3 MiB)
          Interrupt:201 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:10:DC:98:C9:63
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fe98:c963/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:48548 (47.4 KiB)  TX bytes:5748 (5.6 KiB)
          Interrupt:209 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19996 (19.5 KiB)  TX bytes:19996 (19.5 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:64.229.24.189  P-t-P:64.230.197.226  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:13203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:16317069 (15.5 MiB)  TX bytes:887499 (866.6 KiB)

lee@lee-desktop:~$

---

### Post by dmizer on 2006-07-06
okay ... at least that looks right.  i might suggest for you to go to this page: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) and follow the directions there.  not sure it's going to solve your problem or not, but it might.

what is the result of ipconfig in your windows box? (start > run > type: cmd > type: ipconfig)

---

### Post by lee45 on 2006-07-06
ok, ipconfig on windows gave up the ubuntu machine's IP, entering it as gateway made the internet accessible to XP machine. Success!
Thanks for all the help, we been working on this for a week, and you guys got it fixed in six hours!

---

