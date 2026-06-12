---
title: "My servers is not connecting to the internet and I'm not sure what to do about it"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Rafiki123 on 2008-02-12
My ubuntu server will not connect to the internet after the power went out one night. I screwed with some of the settings to change the ip and and reset the network but nothing ive tried that i thought may fix it worked. This computer is plugged into the router by ethernet.

I also can't ping anything. it says unknown host or receive no packets. I ran the cd at boot and tried to rescue a broken system. it said network auto configuration failed. "your network is prob not using DCHP protocol. Alternatively, the DCHP server may be slow or some network hardware is not working prop." I know that my router is using DCHP so thats not it and the network card was working just fine

Can someone walk me through resetting the network settings because apparently I'm not doing it right.

---

### Post by hyper_ch on 2008-02-12
post:

```

cat /etc/network/interfaces

```


```

cat /etc/hosts

```


```

cat /etc/resolv.conf

```


```

cat /etc/hostname

```

---

### Post by Jacques Kleynhans on 2008-02-12
Had the same problem during a power out check if all your router setting are in place my router reset for some reason and yea it toke me a while to figure that out

---

### Post by dstew on 2008-02-12
> I know that my router is using DCHPAre you sure? Maybe your router got its DHCP service disabled by the power outage, or got reset.

---

### Post by Rafiki123 on 2008-02-12
hyper_ch,

Thanks a lot for helping me out. Here are those commands you asked me for:

**for cat /etc/network/interfaces:**
---------------------------------------
#loopback network
auto lo
iface lo inet loopback

#primary network
auto eth0
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.0.255
gateway 192.168.1.254
---------------------------------------
##my routers ip is 192.168.1.1

**for cat /etc/hosts:**
---------------------------------------
127.0.0.1______localhost
127.0.1.1______Nebula.Hell_____Nebula

#the following lines are desirable for IPv^ capable hosts
::1________ip6-localhost___ip6-loopback
fe00::0____ip6-localnet
ff00::0_____ip6-mcastprefix
ff02::1_____ip6-allnodes
ff02::2_____ip6-allrouters
ff02::3_____allhosts

##all of the ___ are spaces
---------------------------------------

**for cat /etc/resolv.conf:**
---------------------------------------
search Hell
nameserver 65.24.7.10
nameserver 65.24.7.11


##Hell is the domain of my router
---------------------------------------

**for cat /etc/hostname:**
---------------------------------------
Nebula
---------------------------------------

Most of this is the stuff that i was trying to edit. I suppose i want to set up a static ip because of toorentflux?

---

### Post by hyper_ch on 2008-02-13
You did give yourself a static IP. The way I see it you need to change the following stuff:

The gateway should be the routers IP --> 192.168.1.1
Broadcast should be (IMHO) --> 192.168.1.255
Not sure about the network one. I'd leave that.

My config looks like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
address 10.0.0.5
netmask 255.255.255.0
gateway 10.0.0.1

```

10.0.0.1 --> router
10.0.0.5 --> my server's IP

---

