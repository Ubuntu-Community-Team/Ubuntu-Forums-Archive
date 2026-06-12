---
title: "connection help"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by threehundred on 2006-11-01
hello. i am having trouble connecting to anything beside a web browser. i cant use gaim or any irc clients or mail clients. i disabled ipv6 in firefox as well as in the modprobe.d aliases file....i added the 3 lines and rebooted but to no avail. does anyone have any idea what it might be? thanks a lot!

---

### Post by adam.tropics on 2006-11-02
Sounds like a firewall/iptables thing, in which case you might want to try [this...]("http://www.ubuntuforums.org/showthread.php?t=290778&highlight=firestarter")

---

### Post by threehundred on 2006-11-02
thanks for the suggestion but i tried it and it did not work. firestarter is not installed on my system. i am at a loss...but i will keep looking around. thanks.

---

### Post by devilsadvocate1987 on 2006-11-02
are you behind a proxy of some sort?

---

### Post by Bartender on 2006-11-02
Was everything OK a week ago?  The u.s. servers have been very unresponsive the last few days.  I think it has something to do with  Edgy downloads, even if you're after dapper repos as I was.

---

### Post by threehundred on 2006-11-02
No I am not behind a proxy, and i installed ubuntu on monday

---

### Post by dbott67 on 2006-11-02
Can you check to see if there's anything set in your Network Proxy settings (System > Preferences > Network Proxy).

Can you post the output of **route -n** and **/etc/resolv.conf**?

Can you connect to the repositories using Synaptic?  Some people have been having issues connecting to the repos and have found this to work.  Obviously, editing the apt.conf file might only affect access to the repositories, but it's something to try:

1. Edit the /ect/apt/apt.conf

```
gksudo gedit /etc/apt/apt.conf
```

2. Remark out the line **Acquire::http::Proxy "false";** by placing a **#** in front of it:
```
**[COLOR="Red"]#[/COLOR]** Acquire::http::Proxy "false";
```

-Dave

---

### Post by threehundred on 2006-11-02
I tried the resolv.conf but i got permission denied. i tried changing my user permissions to root and still got permission denied. and the apt.conf file was empty, there was nothing in it.

here is the route -n

threehundred@threehundred:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.241.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.241.1   0.0.0.0         UG    0      0   



I have DIRECT INTERNET CONNECTION selected for network proxy

advanced config is set to;

localhost
127.0.0.0/8
*.local

---

### Post by dbott67 on 2006-11-02
> **threehundred said:**
> I tried the resolv.conf but i got permission denied. 

Try **cat /etc/resolv.conf**

---

### Post by threehundred on 2006-11-03
i think that worked..


threehundred@threehundred:~$ cat /etc/resolv.conf
search domain.actdsltmp
nameserver 192.168.242.1
nameserver 205.171.3.65

---

### Post by threehundred on 2006-11-04
well, when i said that worked...what i meant was it gave me the results you were looking for...i am still having trouble connecting to anything other than a web browser :)

---

### Post by dbott67 on 2006-11-04
> **threehundred said:**
> well, when i said that worked...what i meant was it gave me the results you were looking for...i am still having trouble connecting to anything other than a web browser :)

Okay, let's try to determine where the trouble lies (such as resolving names (DNS), port blocking (h/w firewall or s/w firewall), etc.).  **I want you to answer these questions and post the output of all of the commands here.**

1. Are you at work, school, home, etc?
2. How are you connected to the internet (cable ,DSL, dial-up)?
3. Do you use a hardware router (D-Link, Linksys, Netgear, etc.)?
4. Besides your web-browser, do any internet-enabled programs work (Synaptic, e-mail, FTP, SSH, telnet?)

**_Firewall Issues:_**
Most employers and schools use some sort of hardware firewalls that are capable of blocking both inbound and outbound traffic.  Many home users also have cable/DSL routers that block unsolicited INBOUND traffic, but generally do not affect outbound traffic.  In addition, there are software firewalls (iptables, firestarter, etc.) that are available to can block both inbound and outbound traffic.

Checking for IPTABLES:
```
sudo iptables -L
```

Checking for something "in the middle" using **traceroute** or **traceping**:

Side note: I think the built-in grahical "Network Tools" version of traceroute uses 'tracepath' (or ping -R) to record the route and it never seems to work for me.  

Here's tracepath:
```
dbott@thedrake:/$ tracepath archive.ubuntu.com
 1:  thedrake.bott.ca (192.168.1.106)                       0.255ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                            asymm  2   0.800ms
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply

[6]+  Stopped                 tracepath archive.ubuntu.com
```

Install **traceroute** from the repositories. 
```
sudo apt-get install traceroute
```

Then do a traceroute to archive.ubuntu.com:
```
dbott@thedrake:/$ traceroute archive.ubuntu.com
traceroute: Warning: archive.ubuntu.com has multiple addresses; using 85.133.25.54
traceroute to archive.ubuntu.com (85.133.25.54), 30 hops max, 40 byte packets
 1  192.168.1.1 (192.168.1.1)  55.205 ms  0.502 ms  0.648 ms
 2  www.xxx.yyy.execulink.net (209.183.xxx.yyy)  14.407 ms  11.819 ms  12.272 ms
 3  i.core1.ip.execulink.net (209.183.xxx.zzz)  14.665 ms  12.594 ms  13.521 ms
 4  67.29.145.41 (67.29.145.41)  23.173 ms  14.492 ms  24.172 ms
 5  so-8-0.hsa1.Detroit1.Level3.net (166.90.248.1)  33.726 ms  22.319 ms  24.113 ms
 6  so-4-3-0.mp1.Detroit1.Level3.net (4.68.115.1)  40.117 ms  24.111 ms  23.371 ms
 7  ae-0-0.bbr1.NewYork1.Level3.net (64.159.1.41)  55.701 ms  48.991 ms  49.774 ms
 8  as-0-0.bbr2.London2.Level3.net (4.68.128.110)  114.971 ms ae-1-0.bbr1.London2.Level3.net (212.187.128.46)  119.086 ms as-0-0.bbr2.London2.Level3.net (4.68.128.110)  113.378 ms
 9  ae-0-51.gar1.London2.Level3.net (4.68.117.11)  114.404 ms ae-0-55.gar1.London2.Level3.net (4.68.117.139)  115.569 ms 4.68.117.43 (4.68.117.43)  115.118 ms
10  195.50.91.142 (195.50.91.142)  115.399 ms 195.50.91.146 (195.50.91.146)  118.422 ms 195.50.91.150 (195.50.91.150)  116.645 ms
11  vlan102.core-l-1.lon2.mnet.net.uk (62.140.218.201)  120.045 ms  117.371 ms  118.385 ms
12  85.133.32.130 (85.133.32.130)  119.217 ms  120.294 ms  119.860 ms
13  85.133.25.54 (85.133.25.54)  122.544 ms  121.542 ms  116.724 ms

```



**_Name Resolution Issues:_**

**1. Ping a known responding server by FQDN**
```
dbott@thedrake:~$ ping www.google.com
PING www.l.google.com (72.14.205.99) 56(84) bytes of data.
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=1 ttl=248 time=26.1 ms
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=2 ttl=248 time=25.7 ms
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=3 ttl=248 time=25.5 ms
64 bytes from qb-in-f99.google.com (72.14.205.99): icmp_seq=4 ttl=248 time=24.6 ms

```

If it is successful, then we know that your DNS servers are able to resolve FQDN to IP.  If not, there is a site called opendns.org.  Just insert the following 2 DNS servers in your **/etc/resolv.conf** file:
* 208.67.222.222
* 208.67.220.220

If you are not on corporate network (work, school, etc.) change your **/etc/resolv.conf** to:
```
gksudo gedit /etc/resolv.conf
```
```
# search domain.actdsltmp
# nameserver 192.168.242.1
# nameserver 205.171.3.65
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Post any relevant output/errors here.

Thanks,
Dave

---

