---
title: "[SOLVED] IP Address problem"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by XXLFazer on 2008-02-14
I am new to this, actually only 3 days old in Linux terms, so answers in baby talk are well accepted...:lolflag:

Firstly just to let you know I am behind a Router and I dual boot with XP Pro

I have a problem, in that, my Linux system (Ubuntu) sees my machine's Local IP addy as 127.0.1.1 BUT my Netgear Router sees it as 192.168.0.2

This seems to be causing me a problem as I run a poker server from Windoze (that I am now running from WINE) that aquires the Global IP addy and then allows users to log in, after I have forwarded the correct port, which is already set up in the router

In Ubuntu, it aquires the Global IP no problem but says the local IP is 127.0.1.1 and not 192.168.0.2 as it should be.

How do I solve this, if at all possible.

Thanks in advance
XXLFazer

---

### Post by hyper_ch on 2008-02-14
127.0.0.1 --> that's always your own machine.

but paste the output of:

```

cat /etc/network/interfaces

```


```

cat /etc/hosts

```


```

cat /etc/hostname

```


```

cat /etc/resolv.conf

```

---

### Post by OffAxis on 2008-02-14
127.0.0.1 is the loopback address; it's the Network Interface Card's self address regardless of the operating system.
In Windows try 
```
ping 127.0.0.1
```

In Linux it would be
```
ping -c 4 127.0.0.1
```

Run 
```
ifconfig
```

This'll list your possible network connections. eth0 is usually the wired port. What's it show?

---

### Post by XXLFazer on 2008-02-14
As requested here's the output of the following

**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

**cat /etc/hosts**
127.0.0.1 localhost richard-desktop
127.0.1.1 richard-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**cat /etc/hostname**
richard-desktop

**cat /etc/resolv.conf**
nameserver 192.168.0.1


Hope this helps you to resolve my problem.

---

### Post by kaiju on 2008-02-14
you /etc/network/interfaces is set to dhcp, which only works if there is a dhcp service running on your server or router, to automatically assign you an ip.

if not, you should have instead of
```
iface eth0 inet dhcp
```
something like
```
iface eth0 inet static
address 192.168.2.101
netmask 255.255.255.0
gateway 192.168.2.1
```
(these are my settings, but i hope you get the picture)

you might also need to change /etc/resolv.conf to have the correct nameserver(s), in case 192.168.0.1 is not working.
e.g i'm using the opendns service and therefore have
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

to change these files, you do a
```
sudo gedit /path/to/file
```

---

### Post by XXLFazer on 2008-02-14
The dhcp service is running on my router as it assigns my IP as 192.168.0.2 and the wife's laptop to 192.168.0.3.
Each new device we connect gets an IP from the router.

Is it possible to edit the /etc/network/interfaces to force the IP as 192.168.0.2 or will this cause a conflict somehow?

---

### Post by zerhacke on 2008-02-14
please post the output of the ifconfig program.

---

### Post by oilchangeguy on 2008-02-14
try unchecking roaming. and set the network to auto config.

---

### Post by kaiju on 2008-02-14
> **XXLFazer said:**
> The dhcp service is running on my router as it assigns my IP as 192.168.0.2 and the wife's laptop to 192.168.0.3.
Each new device we connect gets an IP from the router.

Is it possible to edit the /etc/network/interfaces to force the IP as 192.168.0.2 or will this cause a conflict somehow?

to force a specified ip, you set your eth0 to static, that's all. (i use my router the same way btw.)
so you'll have something like what i posted above, but with your ip and gateway addresses.

---

### Post by XXLFazer on 2008-02-14
ifconfig is as follows

eth0      Link encap:Ethernet  HWaddr 00:19:66:3B:B6:FE
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe3b:b6fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2922652 (2.7 MiB)  TX bytes:876743 (856.1 KiB)
          Interrupt:209 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:872 (872.0 b)  TX bytes:872 (872.0 b)

I am beginning to think that this is a software problem with my poker game and not a configuration problem.

---

### Post by OffAxis on 2008-02-14
> eth0 Link encap:Ethernet HWaddr 00:19:66:3B:B6:FE
inet addr:**192.168.0.2** Bcast:192.168.0.255 Mask:255.255.255.0

There's your ip, properly assigned as 192.168.0.2

So you're right, it seems like a problem with the poker program.

kaiju mentioned this but didn't elaborate so I will; within the router configuration you can assign a specific ip address to your computer based on its MAC address so that every time you turn your computer on it will be assigned the same ip (192.168.0.2).
It's the router's version of creating a static ip in your /etc/network/interfaces file.
It's a little easier to do and more importantly, will work regardless of what operating system you're using.

---

### Post by kaiju on 2008-02-14
hm. i'm guessing your poker program will recognize 127.0.1.1 as the local address no matter what you do to your settings in /etc. besides, if your internet connection is working (and i'm sure it is), there's no point in messing with any settings, so i must apologize for all the misleading suggestions :(
it seems it's either the program itself or wine that needs some adjusting. anyone?

---

### Post by kaiju on 2008-02-14
> **OffAxis said:**
> kaiju mentioned this but didn't elaborate so I will; within the router configuration you can assign a specific ip address to your computer based on its MAC address so that every time you turn your computer on it will be assigned the same ip (192.168.0.2).
It's the router's version of creating a static ip in your /etc/network/interfaces file.
It's a little easier to do and more importantly, will work regardless of what operating system you're using.

this is indeed a much better solution than what i suggested (i wish my cheep router had that option too...)
thanks for clarifying, OffAxis :)

---

### Post by OffAxis on 2008-02-14
> i wish my cheep router had that option too...
wow. didn't think there was a cheaper router out there than my latest POS :)

---

### Post by kaiju on 2008-02-14
> **OffAxis said:**
> wow. didn't think there was a cheaper router out there than my latest POS :)

hehe. there is always something cheaper and worse, trust me :)

---

### Post by XXLFazer on 2008-02-14
Thanks for all the help guys, will have to go and see if there is a solution to my poker software somewhere.
I run a poker league so I need this specific software to work as everyone has the client software on their machines, If I need to keep windoze for the poker then I will, but I will most certainly look for a solution.

**THANKS AGAIN GUYS FOR ALL THE HELP**

---

