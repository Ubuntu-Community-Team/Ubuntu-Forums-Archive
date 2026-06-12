---
title: "internal + external server name"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by cnschulz on 2007-08-20
Hi, 

Noob question...

I have an ubuntu 7.04 headless server up and running with cvs and a bunch of other stuff...

I have an ADSL connection and use NAT to the outside world, so my internal address is 192.168.1.3 and the external is what the ISP gives me.

Ive registered with a free dns provider so i can type xxxx.homeip.net to see my webserver from the net but from my local network i still have to use the machine name.

is there something i can install/configure such that i can reference my server with a single name from the local network and the internet? (id reather not call the machine xxxx.homeip.net either, as that may change in the future.)

sorry its so long winded... didnt know how to explain.

:)

---

### Post by hyper_ch on 2007-08-20
edit your /etc/hosts file as root and add this:

```

127.0.0.1 xxxx.homeip.net

```

---

### Post by cnschulz on 2007-08-20
gday

thats for the machine itself, but other machines on the local network will still resolve externally if the request xxxx.homeip.net.

i think what i need is an internal dns but im not sure...

?

---

### Post by hyper_ch on 2007-08-20
well, if you assing your machine a dedicated IP you could alter each computer's hosts file

[code]
192.168.0.X xxxx.homeip.net
[code]

Or if you have a router you could add there a static route... there are multiple options...

---

### Post by cnschulz on 2007-08-20
oh...  i didnt metion that the local network client is a laptop and goes out of the local network to the internet... thus the hosts file option will not work.

---

### Post by maldojr88 on 2007-08-20
home boy...u need a local dns 
thats the only way ....
the other ways of copying the /etc/hosts file is kind of tedious...
so what i recomend is for you to set up a local dns for the LAN and then have you external DNS, which you already have,for the WAN
so u have 2 dns's which is actually a good thing

---

### Post by asmoore82 on 2007-08-20
> **cnschulz said:**
> oh...  i didnt metion that the local network client is a laptop and goes out of the local network to the internet... thus the hosts file option will not work.

add just the hostname without domain name to the hosts file...

```
#/etc/hosts

# xyz.homeip.net
192.168.1.3   xyz
```
then use just 'xyz' to access when on the LAN and the full 'xyz.homeip.net' from outside.

Also, this is actually just a problem with your router. some brands of routers can handle a
virtual server request to a WAN IP from inside their LAN and others can't.

My default DSL modem's router from a local ISP could not but my DLink WiFi router can.

---

