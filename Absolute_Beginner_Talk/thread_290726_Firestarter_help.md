---
title: "Firestarter help"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by killaray on 2006-11-01
so im trying to share my internet connection and i hear firestarter can allow this... but i have an issue when i try to set it up.. it says that "the device eth0 is not ready" wut does that mean? it also tells me to check network device settings and i dont know where that is, its not in administration... any help plz

---

### Post by SoggyCornflake on 2006-11-01
eth0 is the first ethernet device your kernel detected.  eth1 would be the second etc.

From a command line you can check you ethernet devices by typing
```
ifconfig
```

That should give you some indication where else to look.

---

### Post by killaray on 2006-11-03
still nothing... im not sure wut to do.. i checked ifconfig but then wut?

---

### Post by ice60 on 2006-11-03
> **killaray said:**
> still nothing... im not sure wut to do.. i checked ifconfig but then wut?

see if you can ping your router 
```
ping -c 4 192.168.0.1
```

---

### Post by killaray on 2006-11-03
im not using a router... im tryin to share my internet connection from my PC to Xbox 360.. i have my PC connected to the modem via USB and my Xbox connected to PC via ethernet.. it worked on windows i just dont know how to enable it on Ubuntu

---

### Post by NetworkGuy on 2006-11-03
We need to determine what Linux has called your USB and yout Ethernet connection.   Pleae post the output of an ifconfig done from the terminal.

---

### Post by killaray on 2006-11-03
```
eth0      Link encap:Ethernet  HWaddr 00:11:5B:D3:09:F8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12018 (11.7 KiB)  TX bytes:1152 (1.1 KiB)
          Interrupt:185 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:14:F8:47:2C:D7  
          inet addr:69.120.102.199  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::214:f8ff:fe47:2cd7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1488220 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:464739631 (443.2 MiB)  TX bytes:14091039 (13.4 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51462 (50.2 KiB)  TX bytes:51462 (50.2 KiB)

```

---

### Post by killaray on 2006-11-04
everyones gone for the weekend?

---

### Post by killaray on 2006-11-05
can anyone help me out with this i really wanna get my Xbox connected

---

### Post by SoggyCornflake on 2006-11-06
> **killaray said:**
> everyones gone for the weekend?

Guess so.  Sorry for not following up.

Just to be clear, Is the ethernet device you're using with your Xbox embedded on your motherboard, installed as a PCI card, installed as a PCMCIA (PC Card) or USB device?  Just want to be sure that the ethernet card is supported by Ubuntu.  If it isn't there's still some things that could be done, but it will take a lot more work.

Assuming it is supported then you can move on.

I'm not sure if this will help, but I did a quick search for Firewall Howto on Ubuntu, and got this link: [http://www.ubuntuforums.org/showthread.php?t=159661&highlight=firewall+howto]("http://www.ubuntuforums.org/showthread.php?t=159661&highlight=firewall+howto")

The script seems to explain how to do a firewall without using firestarter which implies a lot more hands on for you, but maybe it will get you going.

From what I can tell, everywhere the script shows an example of eth0, you'd need to put eth1 and vice versa since I think eth0 is the network card connecting to your Xbox,and eth1 is your modem.

Hang in there.:)

---

### Post by killaray on 2006-11-06
the ethernet is enbedded in my MoBo, ima give that how to a try and then ill get back to u

---

### Post by killaray on 2006-11-06
tried it out and nothing yet

---

### Post by killaray on 2006-11-08
ive tried several guides to no avail.. can anyone help me out? dyin wit no xbox here

---

### Post by killaray on 2006-11-08
i did some precedure, forgot off of which guide and it changed my IP address, i know that the computer is now picking up the Xbox cause when i turn it on it says theres a new connection

---

