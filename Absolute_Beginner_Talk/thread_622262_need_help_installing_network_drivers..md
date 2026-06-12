---
title: "need help installing network drivers."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by kuzba on 2007-11-24
i have a .bz2 package of my Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller

i am a complete noob at ubuntu and have no idea how to install it.

could someone please walk me through the install?

all i know is that i need to type certain commands into terminal.

i read the readme but couldnt understand it.

can anyone help?

thanks

---

### Post by markharding557 on 2007-11-24
usually ethernet is installed automaticaly in ubuntu,does yours not work?

---

### Post by HermanAB on 2007-11-24
Uhhh, this isn't easy - 99% of the problem is that the device driver code of Linux is constantly changing, so you need to do some sleuthing to get it figured out - practically all howto guides on the web are wrong. Do some googling and reading before you try to continue, especially read the Ethernet Howto on ltsp.org but bear in mind that all the little details may be wrong to some degree...

Basically, all you need to do is put the driver somewhere, then list it in modules.conf or conf.modules, or modules.cf or whateverthebloodyhelltheyarecallingitthisyear, then restart networking.

'Hope that helps!

H.

---

### Post by kuzba on 2007-11-24
> **markharding557 said:**
> usually ethernet is installed automaticaly in ubuntu,does yours not work?

nah. im in a network anyway so i have changed the settings to use a static ip. im pretty sure thats what i have.

the only thing i can think of doing is installing the drivers. when i ping the gateway ip it says host unreachable. what would that mean?

---

### Post by markharding557 on 2007-11-24
change it to dchp and it should find your gateway.
host unreachable means you're not connected to the gateway

---

### Post by kuzba on 2007-11-24
ok ill try that and then report back.

---

### Post by kuzba on 2007-11-24
nah didnt work.

i also tried setting firefox to automatically detect conection...

---

### Post by elctb on 2007-11-24
Open a terminal and type the following commands "ifconfig" and "netstat -rn". Post the output of the above commands.

---

### Post by kuzba on 2007-11-24
eth0      Link encap:Ethernet  HWaddr 00:16:E6:6A:D5:1C  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7370 (7.1 KB)  TX bytes:3325 (3.2 KB)
          Interrupt:20 

eth0:avah Link encap:Ethernet  HWaddr 00:16:E6:6A:D5:1C  
          inet addr:169.254.7.1  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)




























Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0.0         0.0.0.0         U         0 0          0 eth0

---

### Post by elctb on 2007-11-25
It seems you're connected to an ipv6 network. It could be that the current driver doesn't support ipv6 and that's why you need to install the .bz2 package, but I can't really say for sure.

Do you have a link to download the .bz2 driver ? I'd like to take a look to figure out what's going on.

Also, to add ipv6 addresses you need to use this format:
ifconfig <interface> inet6 add <ipv6address>/<prefixlength>

---

### Post by kuzba on 2007-11-26
i uploaded the driver folder.

[http://www.mediafire.com/?93vy1n93p9c](http://www.mediafire.com/?93vy1n93p9c)

---

### Post by elctb on 2007-11-26
I took a look at the driver sources. It's not too difficult to install, but I didn't see any reference to ipv6 which leads me to believe that it might be a configuration problem.

What's the computer connected to ? I assume it's connected to a dsl/cable modem, right ?

Can you also try the following ?:

```
sudo ifconfig eth0 down
netstat -rn
sudo dhclient eth0
ifconfig
netstat -rn
```

Make sure you post all the information displayed by the above commands if it still doesn't work.

---

