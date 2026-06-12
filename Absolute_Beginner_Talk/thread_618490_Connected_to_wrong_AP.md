---
title: "Connected to wrong AP"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Vamp381 on 2007-11-20
I have one problem.My wireless connection is connecting to wrong Ap,is there any command or software that can scan other ap (connection is eth0).

---

### Post by OffAxis on 2007-11-20
```
sudo iwlist eth0 scan
```
will list all access points in range.
eth0 = your connection's name

To connect to one:
```
sudo iwconfig eth0 ESSID [your access point's name]
```
assuming there's no security.
eth0 = your connection's name

```
man iwconfig
```
will list all the available options. You might also be interested in the **ap **option.

---

### Post by HermanAB on 2007-11-20
Configure the ESSID properly.

Cheers,

H.

---

### Post by Vamp381 on 2007-11-20
When i entered 

```
sudo iwlist eth0 scan
```

i get:

```
pavle@pavlee:~$ sudo iwlist eth0 scan
eth0      Interface doesn't support scanning.
```

I`m connected to internet now and i used this command to enable it

```
sudo pppoeconf
```

---

### Post by Inxsible on 2007-11-20
That could be because your eth0 is your LAN. try using ***eth1*** in the same commands

---

### Post by Vamp381 on 2007-11-20
I get the same.
eth1      Interface doesn't support scanning.

---

### Post by Inxsible on 2007-11-20
> **Vamp381 said:**
> I get the same.
eth1      Interface doesn't support scanning.you do have wireless built in to your machine right ?

---

### Post by Vamp381 on 2007-11-20
Yes i have.

---

### Post by OffAxis on 2007-11-20
is it your only connection?
or are you jacked in on the wired connection?

---

### Post by Inxsible on 2007-11-20
I think its probably because you are using another connection, probably a dial up since you said you enabled it with pppoeconf

---

### Post by Vamp381 on 2007-11-20
eth0      Link encap:Ethernet  HWaddr 00:11:2F:D1:40:75  
          inet addr:192.168.1.248  Bcast:192.168.1.255  Mask:255.255.254.0
          inet6 addr: fe80::211:2fff:fed1:4075/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37083940 (35.3 MiB)  TX bytes:4339625 (4.1 MiB)
          Interrupt:19 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:976 (976.0 b)  TX bytes:976 (976.0 b)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.5.10.156  P-t-P:10.5.20.156  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1488  Metric:1
          RX packets:31386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:35507665 (33.8 MiB)  TX bytes:3651251 (3.4 MiB)


That i get when i entered if config.Yes it only connection

---

### Post by Inxsible on 2007-11-20
i dont see a wireless extension.

---

### Post by OffAxis on 2007-11-20
> That i get when i entered if config

what does 

```
iwconfig
```

yield?

---

### Post by Vamp381 on 2007-11-20
pavle@pavlee:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.


Its like i don`t have connection.My cable is connected to card on roof (i think is via something) and antena is directed in right way,,is there any other way to enable connection ? maybe i done something wrong.

How to get screen shot of desktop.In network tools its showing received packets,receivet bytes etc.

---

### Post by OffAxis on 2007-11-20
> My cable is connected to card on roof

I'm a little confused.

What's your setup? (and please specify wired and wireless parts)

---

### Post by Vamp381 on 2007-11-20
VIA tecnhologies, Inc. VT 6102 [Rhine-II] (Rev 78).
I don`t know name of antena and think name of card on roof begin something Wlink

---

### Post by OffAxis on 2007-11-20
okay, so it goes your computer wired to --> dsl wired to card/antenna--> wireless to a city wi-fi access point?

---

### Post by Vamp381 on 2007-11-20
Yes i start connection by tiping

```
pon dsl-provider
```

---

### Post by OffAxis on 2007-11-20
The
```
iwconfig
```
command is only for wireless network cards. Since you're connecting to your ISP via a DSL modem through your wired connection the wireless specific commands never come into play.

---

### Post by Inxsible on 2007-11-20
yeah, you do not have a wireless card on your machine, like I suspected before.

---

