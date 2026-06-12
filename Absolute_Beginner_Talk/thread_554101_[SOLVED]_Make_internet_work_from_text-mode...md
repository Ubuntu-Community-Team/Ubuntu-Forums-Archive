---
title: "[SOLVED] Make internet work from text-mode.."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Mollier on 2007-09-18
Hey, I'm trying to install Ubuntu 7.04. X server is not working, and I'm trying to fix it using wget [http://mylittleubuntuguide.com/files/ati](http://mylittleubuntuguide.com/files/ati) etc. 
The thing is that I can't even ping that site, meaning that there is no internet connection i assume..
How can I turn this on via the text mode? 
Preferably a wireless connection, but at this point anything will do..Thanks

---

### Post by kelnage on 2007-09-18
Right, to start with, I'd type:

```
ifconfig
```

Into the console and post up the results. Also, could you let us know your system specification and the network adapters you are trying to use (Ethernet, Wireless (A, B or G?), etc.). 

If you're trying to use an Ethernet cable, does the socket light up when you connect the cable? If you're on wireless, is there any kind of security?

---

### Post by Mollier on 2007-09-18
I get a whole lot of things  when I write ifconfig. I tried print screening but that didn't work. Is there a way of copying everything on the screen while in text mode?

I saw eth01 and eth02..

I have a Wireless 802.11g with a WEP encryption..

Is this the information needed?

Thanks!

---

### Post by kfrance on 2007-09-19
you can capture it in a file and then look at it, copy it, etc. Try>  ifconfig > config.txt This capture the output and writes it to the file config.txt. You can call the file whatever you want.

---

### Post by HermanAB on 2007-09-19
Let's assume:
IP = 192.168.1.10
Netmask = 255.255.255.0
Gateway = 192.168.1.1
DNS = 172.16.1.1

To set that up from the command line:
$ sudo -i
password
# ifconfig eth0 192.168.1.10 netmask 255.255.255.0 up
# echo "nameserver 172.16.1.1" > /etc/resolv.conf
# route add default gw 192.168.1.1
# nslookup [www.yahoo.com](www.yahoo.com)

La voila!

H.

---

### Post by Mollier on 2007-09-19
I could not make it work.Here is what I tried:

I'm trying to set up a dual boot, that meaning that Windows is working properly.
I went to windows and found out this:

IP: 192.168.0.144
Netmask: 255.255.255.0
Standard gateway: 192.168.0.1
DNS Servers: 62.97.193.3 and 192.168.0.1

Is that the info I'm supposed to use?

A bit more info about my setup:

I have a DI-524 wireless router and two pc's.One desktop and a laptop, I'm trying to set Ubuntu up on a laptop. I did what you told me, but when trying the nslookup it didn't work..Any ideas what may be wrong?

I really appreciate your help, thanks!

---

### Post by Mollier on 2007-09-20
Bumb, anyone, I'm really stuck...

---

### Post by Mollier on 2007-09-22
Fixed it by reinstalling with my pc wired up to the router. After the install I followed mylittleubuntuguide.com and it works like a charm..

---

