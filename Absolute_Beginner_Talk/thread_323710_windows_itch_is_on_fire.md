---
title: "windows itch is on fire"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by source on 2006-12-22
(I posted this in the wrong section earlier)

Im trying create a network bridge and its not working. :(

I have my connection set up like so


                                                               Xbox 360 < ------------ PC <----------ROUTER<----dsl modem


I connect my PC to my xbox with an ethernet cable (rj-45)

I basically do not have the space to connect the router directly to my PC and must bridge from my PC to the xbox.


I am all wired and no wireless so my eth0 and eth1 are both wired. eth0 wasnt showing up for me till i assigned it as static and even then the xbox wasnt connected.(im guessing cause i assigne dit the wrong static ip) 

could someone please tell me the gateway subnet mask, DNS, IP address, etc i need to configure on my xbox and pc?

my Working configuration for the Xbox using ethernet direct to router was
```
IP Address 192.168.1.100 
Subnet Mask 255.255.255.0
Gateway 192.168.1.1
primary DNS server 192.168.0.1
secondary DNS server 0.0.0.0

```


My working PC configuration is
```
eth1 =address DHCP
eth 2 address DHCP
DNS server 192.168. 0.1
```

?](*,) :-k :confused:

---

### Post by D_jmc on 2006-12-22
Might be a bit of a no brainer, but are you using a crossover cable or a straight through, If your connected from pc to xbox, you need to use a crossover cable.

---

### Post by source on 2006-12-22
yes i am using a crossover from my pc to my xbox and an ethernet from my router to my pc.

i have the necessary hardware

its the software thats the problem....

---

