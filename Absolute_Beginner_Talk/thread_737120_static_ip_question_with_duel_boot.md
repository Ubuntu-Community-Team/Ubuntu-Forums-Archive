---
title: "static ip question with duel boot"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by 888mafia on 2008-03-27
Ok i have ubuntu (gutsy) installed with a duel boot (xp-kubuntu) on desktop cable modum + a router for laptop
i would like to get a static ip for desktop when i run my ubuntu server but i need another ip for laptop yes 

ok as i read my own post i can see it dose not make much sense but i don't quite know how to explain it  
Ok what im doing is i want to stream a radio show from my server from my desktop(ubuntu) and i would like to do the show from my laptop where i could do the show mobil could any one explain to me what it is i need to do or buy or if it is possible. 
thank you ahead of time

---

### Post by ghost_ryder35 on 2008-03-27
on the server edit the interfaces file to get a static ip
```
sudo vi /etc/network/interfaces
``` 

you will see
```

auto eth0  ##you need to do this to whatever interface you need to apply the static IP too.  In this example we will assume it is the most common one "eth0"
iface eth0 inet dhcp

```

change it to
```

auto eth0
iface eth0 inet static
        address 192.168.1.100  * ##whatever you want you ip address to be*
        netmask 255.255.255.0  *## your subnet mask*
        network 192.168.1.0    * ##your network address*
        broadcast 192.168.1.255  *##broadcast will always be the last ip address of the subnet range*
        gateway 192.168.1.1  *##your routers address*

```

A "vi" cheat sheet [http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

---

### Post by 888mafia on 2008-03-27
ill try right now ty so much

---

### Post by ghost_ryder35 on 2008-03-27
> **888mafia said:**
> ill try right now ty so much

no problem, let us know the outcome

P.S. if you have never used "vi" before it can be tricky  here is a link to a great website with the commands for "vi"
[http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)
remember before exiting hit the "ESC" key and then "Shift + Z + Z" this will save and exit :)

---

### Post by 888mafia on 2008-03-27
> **ghost_ryder35 said:**
> on the server edit the interfaces file to get a static ip
```
sudo vi /etc/network/interfaces
``` 

you will see
```

auto eth0  ##you need to do this to whatever interface you need to apply the static IP too.  In this example we will assume it is the most common one "eth0"
iface eth0 inet dhcp

```

change it to
```

auto eth0
iface eth0 inet static
        address 192.168.1.100  * ##whatever you want you ip address to be*
        netmask 255.255.255.0  *## your subnet mask*
        network 192.168.1.0    * ##your network address*
        broadcast 192.168.1.255  *##broadcast will always be the last ip address of the subnet range*
        gateway 192.168.1.1  *##your routers address*

```

A "vi" cheat sheet [http://www.lagmonster.org/docs/vi.html](http://www.lagmonster.org/docs/vi.html)

mine is difrent

```
auto lo inet loopback
```

confused about this

```
 address 192.168.1.100  * ##whatever you want you ip address to be*
        netmask 255.255.255.0  *## your subnet mask*
        network 192.168.1.0    * ##your network address*
        broadcast 192.168.1.255  [I]##broadcast will always be the last ip address of the subnet
``` 

do ineed to get this  info from my router then  change it or do i just make it up create my own.
 netmask 255.255.255.0 
 network 192.168.1.0    dose it stay the same as now
?????  way confused forgive me i only a week old user

---

