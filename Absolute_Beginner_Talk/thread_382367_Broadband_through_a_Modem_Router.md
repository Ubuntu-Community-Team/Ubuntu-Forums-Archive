---
title: "Broadband through a Modem Router"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Brian R. on 2007-03-12
Have windows xp on one machine, ubuntu 6.06 on another, hooked together through a "NetComm" Modem Router an RJ45 type.
The two machines can see each other and access files in their shared folders. The windows machine can connect to the internet. but I cannot get the ubuntu machine to connect to the internet, it can ping the other machine and the Modem Router.
The addresses are
Modem Router 192.168.1.1 set by the ISP
Windows         192.168.1.2 set by me
ubuntu            192.168.1.3 set by me
I do not have a static IP address
The network settings on the ubuntu machine show DNS Servers
203.12.160.35
203.12.160.36
What ever that is supposed to mean
Need help thank you

---

### Post by shareMenaPeace on 2007-03-12
To configure ubuntu open a terminal and run

```
sudo pppoeconf
```

---

### Post by dhughes on 2007-03-12
> **Brian R. said:**
> Have windows xp on one machine, ubuntu 6.06 on another, hooked together through a "NetComm" Modem Router an RJ45 type.
The two machines can see each other and access files in their shared folders. The windows machine can connect to the internet. but I cannot get the ubuntu machine to connect to the internet, it can ping the other machine and the Modem Router.
The addresses are
Modem Router 192.168.1.1 set by the ISP
Windows         192.168.1.2 set by me
ubuntu            192.168.1.3 set by me
I do not have a static IP address

 That looks good to me, DHCP gives your Ubuntu machine an IP address. I assume both use a subnet mask address of 255.255.255.0 too.

 In a Terminal what does ifconfig show?


> 
The network settings on the ubuntu machine show DNS Servers
203.12.160.35
203.12.160.36
What ever that is supposed to mean
Need help thank you

  Is the IP of the DNS server your ISP uses, it just converts [www.yahoo.com](www.yahoo.com) into 69.147.114.210 or whatever the real IP address of yahoo is. As long as those are the valid IP addresses of a DNS server it should work, you can set it in your router too. As an alternative you can also use DNS servers other than those of your ISP such as the ones at Open DNS.

 I'm not sure why you can't connect.

---

### Post by Brian R. on 2007-03-12
Tried that and this is the answer i got.

Sorry, I scanned 1 interface, but the Access 
Concentrator of your provider did not respond. 
Please check your network and modem cables.
Another reason for the scan failure may also be another running pppoe 
process which controls the modem.

---

### Post by freebird54 on 2007-03-12
Are you sure it is a 'modem connection'?  Sounds to me like a wired connection - the fact that there is a modem in the loop probably has nothing to do with what your computer needs to know...

Whenever I see 192.168.1.1 I assume the router is the only thing you will see on the way out to the net..

Try setting the Ststem->Administration->Networking to wired and see what you get..

Hope that helps - if not - some more digging required.....

---

### Post by dineshs on 2007-03-12
I think your modem is configured.try by making it bridged.

---

### Post by Brian R. on 2007-03-12
Thanks for all the help, but it is now working, i do not know what i did, but i went into the modem configuration set up had a look at a few things, it then found the ubuntu machine and every thing worked after that.

---

