---
title: "Can't connect to Internet though wired connection"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by madfrageris on 2006-12-23
Hello,

I have two computers and a router, connected to each other. While every computer is running Windows XP, they ping and both have Internet. When I run Ubuntu on one of the PCs, I have the wired connection, I can ping the other computer with Windows, as the other computer can ping Ubuntu, and I can ping other Internet addresses, [www.google.com](www.google.com) for instance. Furthermore, it shows that it sends/receives some packages.

Yet Ubuntu doesn't have the Internet at all. It is strange, because every settings are set to be obtained automatically and are working fine in Windows :(.

Maybe there's some sort of network setup wizard as in Windows?

Oh, to illustrate how everything is set:
[http://img165.imageshack.us/img165/6301/untitlednp6.jpg](http://img165.imageshack.us/img165/6301/untitlednp6.jpg)

---

### Post by thomasaaron on 2006-12-23
Try:

sudo ifup eth0

---

### Post by mjm115 on 2006-12-23
Can you copy and paste the results of 'ifconfig' in a terminal from Ubuntu here?

---

### Post by madfrageris on 2006-12-23
"sudo ifup eth0" returns:
```
ifup: interface eth0 is already configured
```

"sudo ifconfig eth0" returned:
```

eth0   Link encap:Ethernet HWaddr 00:13:D4:BF:A3:7E
         inet addr:192.168.1.3 Bcast:132.168.255 Mask:255.255.255.0
         inet6 addr:fe80::213:d4ff:febf:a37e/64 Scope:link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:326 errors:0 dropped:0 overruns:0 frame:0
         TX packets:490 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:33268 (32.4 KiB) TX bytes:36690 (35.8 KiB)
         Interrupt:185 Base address:0x6400
```

Was hell a lot of paperwork :D.

---

### Post by cbudden on 2006-12-23
I think your Ubuntu system may not have the correct DNS addresses.  Does your router have them?  If not you should enter them manually.  Look in System -> Admin -> Networking, and look on the DNS tab.

---

### Post by madfrageris on 2006-12-23
> **cbudden said:**
> I think your Ubuntu system may not have the correct DNS addresses.  Does your router have them?  If not you should enter them manually.  Look in System -> Admin -> Networking, and look on the DNS tab.

Where should I look for the proper DNS server address to type?

---

### Post by cbudden on 2006-12-23
If your windows machine is correctly getting them, you could look on there.  Start -> run, type cmd and then type ipconfig.  Look for the dns server addresses.  If you can't find them on there, log onto your routers interface (192.168.x.x, or 10.0.0.x something) and have a look around there.

---

### Post by madfrageris on 2006-12-23
Right, using "ipconfig" in Windows does following:

```

Connection-specific DNS Suffix  . :
IP Address. . . . . . . . . . . . : 192.168.1.2
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.1.1

```

In my router settings "Primary DNS" is set to 192.168.1.1, but the "Preffered DNS server" in other tab shows "212.59.0.1", the alternate: "212.59.0.2". So which is the right one?

---

### Post by cbudden on 2006-12-23
Try with the 212 addresses, put both of them in the list for Ubuntu.  Try this ip - 64.233.161.104 it is google.  If it is a DNS problem then that should still load.

---

### Post by madfrageris on 2006-12-23
I've put "212.59.0.1" into DNS tab in Networking options and the Internet connection appeared. Thank you cbudden :)

---

### Post by cbudden on 2006-12-23
Your welcome madfrageris

---

### Post by madfrageris on 2006-12-23
Now... that's strange, but my settings keep resetting to the old 192.168.1.1 from time to time. I manually change it back to 212.59.0.1, but it happens sometimes.

What can I do about this?

---

