---
title: "Sudo, hostname resolution and network connection"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by mooz on 2006-11-06
Hello everibody. Excuse me for my poor english but in my-language-forums I didn't find any solution to my problem with my ubuntu dapper. When I'm connected to the network I can't use sudo since it comes with the message:

> sudo: unable to lookup sedek via gethostbyname()

I tried to follow solutions than I found on the internet, but none of these worked in my case. I report here my configuration files:

> **/etc/hosts**
127.0.0.1 localhost.localdomain localhost.localdomain sedek
192.168.1.54 localhost.localdomain localhost.localdomain sedek

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts


> **/etc/hostname**
sedek


> **/etc/network/interfaces**
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.37
netmask 255.255.255.0
gateway 192.168.1.1


iface eth1 inet static
address 192.168.1.54
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.1.255
gateway 192.168.1.1

# auto eth2
# iface eth2 inet dhcp

# auto ath0
# iface ath0 inet dhcp

# auto wlan0
# iface wlan0 inet dhcp


# auto eth1


I think that there is something that is just not working about host names resolution when I use a static IP address, but I can't understand what. I also used DHCP and all seemed to work fine when I connected using this; also all my internet requestes where faster using DHCP. However I need to use a static Ip addres, so any help will be very appreciated!

---

### Post by bodhi.zazen on 2006-11-06
I am not sure, but did you try commenting out:

192.168.1.54 localhost.localdomain localhost.localdomain sedek

```
#192.168.1.54 localhost.localdomain localhost.localdomain sedek
```

Then re-boot and re-try.

---

### Post by bettlebrox on 2006-11-06
localhost should only be assigned to the 127.0.0.1 .

---

### Post by mooz on 2006-11-06
I added the row of "192.168.1.54" when I was trying to resolve this problem. However I tried to comment and it didn't work. I tried also to make it:

> 
192.168.1.54 sedek


but this didn't work yet.  ](*,)

I forgot to tell that I assigned a password to root account using the command:

> sudo passwd [password]

could this be part of the problem?

---

### Post by bettlebrox on 2006-11-06
Setting the root password shouldn't cause networking problems.

The first line of /etc/hosts should look something like this:

127.0.0.1 localhost.localdomain localhost mylaptop

And remove this line:
192.168.1.54 localhost.localdomain localhost.localdomain sedek

Can you post the output of "ifconfig -a"? 

U do know that you have 2 network interfaces enabled? eth0 & eht1? They're both on the same network, 192.168.1.*, which is bound to cause some routing problems.

---

### Post by mooz on 2006-11-07
The interface eth0 is the one of my wired ethernet card; it should be disable (as if I gave the command ifconfig eth0 down) when the cable is unplugged, shouldn't it? I'll try to set up auto-configuration and I'll post the output of ifconfig when I'll be home. 

Another strange thing that I've noticed is that I can't ping my own host when I'm connected to the internet using its hostname or the name localhost (when it's all fine if I use ip addresses). It says me "Destination host unreachable".

---

### Post by mooz on 2006-11-07
Here is the output from my ifconfig -a and the output from my route:

> 
root@sedek:/home/aldo# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

root@sedek:/home/aldo# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:2F:83:3A:D6
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:11:2F:9C:AE:1C
          inet addr:192.168.1.54  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe9c:ae1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:400376 (390.9 KiB)  TX bytes:2669 (2.6 KiB)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


I tried to set up eth0 interface in auto-configuration but this didn't work. What is that sit0 interface?

---

