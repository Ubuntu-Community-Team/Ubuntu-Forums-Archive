---
title: "code for getting connected to internet"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by tollboy on 2007-12-02
i recentl installed ubuntu it is showing connectivity with a wired network bt
when i try to open any web site it is not opening.
please tell me the code for terminal to type for connecting to net

---

### Post by mellowd on 2007-12-02
open up a terminal and type this:

```
ifconfig
```

Could you please paste the reults here?

---

### Post by nickoli_02 on 2007-12-02
try this

```
ping www.google.com
```

if you get a response your connection is working fine. if you dont get a response and you're behind a router, try pinging the ip address of the router. it's usually 192.168.1.1

---

### Post by mellowd on 2007-12-02
Also, install traceroute and trace out. see how far you get.

First

```
sudo apt-get install traceroute
```


then 

```
traceroute www.google.com
```

---

### Post by daimaru on 2007-12-02
you may have to specify your nameserver (if you can ping your router , but no dns adresses like [www.google.com](www.google.com)) then edit your /etc/resolv.conf file and insert your routers ip address as the nameserver .

---

### Post by tollboy on 2007-12-02
i tried this one
ping [www.google.com](www.google.com)
bt this is nt working 
it is pinging with modem at 192.168.1.1
bt nt with google

---

### Post by mellowd on 2007-12-02
have you traced yet? And what about your ifconfig?

---

### Post by tollboy on 2007-12-02
when i tried ifconfig then many things r cm in outcome
the only thingh i understood is that it is written 0 errors,0dropped,0overruns
and for traceroute it is saying that package is missing,has been obsoleted, or is only available from another source

---

### Post by mellowd on 2007-12-02
Paste the output of ifconfig here so I can take a look


secondly, as I said, you need to install traceroute first:

```
sudo apt-get install traceroute
```

---

### Post by tollboy on 2007-12-02
that was on other comp i cant paste it anyway
evem with screen shot too
can u just tell me the command which is like[COLOR="Red"] pppoe [/COLOR]smthingh like that
i alredy told abt traceroute in previous podt

---

### Post by daimaru on 2007-12-02
i really dont know why i m posting this since you dont seem to read the posts. but here it goes
the most likely thing is that your gateway is not set up or your nameserver is not registered. 
to check your gateway type:
```
**route** 
```
your router should be listed there as 192.168.1.1 if not add the gateway with 4th command below.

if your using dynamic dhcp ip:
```
**dhcpcd eth0**
```for static ip: (use 2-255 at the end)
```
**ifconfig eth0 192.168.1.2**
```to enter your nameserver:
```
**echo nameserver 192.168.1.1 > /etc/resolv.conf**
```to setup your gateway: assuming your NIC is eth0
```
**route add default gw 192.168.1.1 eth0**
```

---

