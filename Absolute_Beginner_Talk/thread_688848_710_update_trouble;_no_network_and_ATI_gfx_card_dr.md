---
title: "710 update trouble; no network and ATI gfx card drivers"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by doopey on 2008-02-05
ello.

i installed ubuntu using wubi 7.04 ( [http://wubi-installer.org/](http://wubi-installer.org/) ), and just updated to v. 7.10 (automatic updater)
upon rebooting i got a couple of error messages (when finished booting into GNU)
i also didn't have internet access, and i got a warning for my ATI catalyst drivers.

all i really need is help on how to manually fix the network driver so i can get back online, then i guess the starting errors will magically dissapear and i can start looking into the ATI bit


my network card is a built-inn LAN card integrated in SiS735, (motherboard k7s5a)

any help apprechiated

---

### Post by talsemgeest on 2008-02-06
Take a look here: [http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

---

### Post by doopey on 2008-02-06
thank you for the guide, but i dosnt say anything about setting up the networkcard driver.
as far as i understand ubuntu comes with the drivers needed. how do i see which is installed/select the correct one?

---

### Post by gun_p on 2008-02-06
Did you enable the restricted drivers?
If thats not the case, you might want to try that.

---

### Post by jan quark on 2008-02-06
run 

```
lshw -C network
```

and post the result please

this command tells you what network drivers you are using currently

---

### Post by doopey on 2008-02-06
seems the network drivers are ok, same as windows atleast


> mushin@anarchon:~$ lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet 

interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       

physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 90
       serial: 

00:0a:e6:2d:67:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list 

ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 

ip=10.0.0.9 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes




---------------------------------------------------------------------


mushin@anarchon:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:2D:67:3D  
          inet addr:10.0.0.9  Bcast:10.0.0.255  

Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe2d:673d/64 Scope:Link
          UP BROADCAST 

RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:541 errors:0 dropped:0 overruns:0 frame:0
       

   TX packets:426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:2 txqueuelen:1000 
          

RX bytes:367022 (358.4 KB)  TX bytes:47981 (46.8 KB)
          Interrupt:18 Base address:0xdc00 

lo        

Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 

Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 

overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 

txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

-------------------------------------------------------------------


etc/hosts


127.0.0.1	localhost
127.0.1.1	anarchon.lan	anarchon

# The following lines are desirable for 

IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 

ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



-------------------------------------------------------------------


etc/network/interfaces


# This file describes the network interfaces available on your system
# and how to activate them. For more 

information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary 

network interface

#iface eth0 inet dhcp

iface eth0 inet dhcp

auto eth0


-there is also a interfaces.bak-0 

file, but i am unable to rename it to try and use the backup?

# This file describes the network interfaces 

available on your system
# and how to activate them. For more information, see interfaces(5).

# The 

loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 

inet dhcp




------------------------------------------------------------------
-

ping localhost works


mushin@anarchon:/etc/network$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from 

localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.071 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 

ttl=64 time=0.063 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.062

-------------------------------------------------------------------


---

