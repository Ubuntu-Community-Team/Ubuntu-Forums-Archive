---
title: "Basic internet stuff"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by natman on 2006-10-10
Hi, 
I am in an office, and we need a printer server computer and i have set up ubuntu on a pc and it runs fine. My question is that im not sure if the internet is working on it, when i got to system - admin i see that eth0 is active ( i have an ethernet cable at the back ).
But when i click firefox its says error for each page i try .

So does is my computer able to connect to the net but just missing the right settings?, if so how do i go about changing the settings.

Also any ideas on how to make it a printer server for windows/ubuntu computers?

Thanks:

---

### Post by Endwin on 2006-10-10
You can take a look and see. if you type 

```
ifconfig
```

That will tell you if you have an IP address for eth0. If you do try pinging another computer on the network.

```
ping XXX.XXX.XXX.XXX
``` 

Replace XXX.XXX.XXX.XXX with the IP of a machine on the local network. If you can't browse the net, since you said you were in an office did your sys admin set up some sort of proxy server that you need to use? You might nt get an IP because your machine is not allowed to access the network.

As for printer sharing check out samba. You can enable file and printer sharing and then share the printer.

---

### Post by Iowan on 2006-10-10
Under the System>Administration>Networking section you mentioned...
Is eth0 configured for DHCP or for a static address?
(ipv6 can cause problems, but first things first)

---

