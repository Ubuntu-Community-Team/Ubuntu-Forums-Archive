---
title: "Apache Problems"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by splendid on 2006-10-02
I have Apache setup, and I am trying to access using my DynDns URL.  I have opened up Port 80 on my router.  I can access the page through [http://localhost](http://localhost) and [http://127.0.0.1](http://127.0.0.1)

Also, I am able to access using the port on my router 192.168.0.100

Tried looking at the configuration files.  Not sure what else to check.

---

### Post by firefly2442 on 2006-10-02
If you have a dynamic IP address and are using DynDNS, "ddclient" is a nice easy update client that works well under Ubuntu.  Just apt-get install it.  Can other people outside your local network access your webpage?  Make sure the IP address that DynDNS is using isn't a local IP address like 192.168.X.X but something public so that other people on the Internet can get to it.  HTH. :)

---

### Post by sabitha on 2006-10-02
> **firefly2442 said:**
> If you have a dynamic IP address and are using DynDNS, "ddclient" is a nice easy update client that works well under Ubuntu.  Just apt-get install it.  Can other people outside your local network access your webpage?  Make sure the IP address that DynDNS is using isn't a local IP address like 192.168.X.X but something public so that other people on the Internet can get to it.  HTH. :)

just newbie question : 
how do i know local IP and public IP ?

---

### Post by JamesVeDe on 2006-10-02
Most private IPs will start 192.168

---

### Post by firefly2442 on 2006-10-03
Try going to the terminal and typing "ifconfig".  This will tell you your IP address.  Like JamesVeDe stated, private IPs usually start with 192.X.X.X

127.0.0.1 is considered your "localhost" or local machine IP address.  Make sure it's not using this one because then only you will be able to see your website. :D

---

### Post by Josh1 on 2006-10-03
And your global IP can be found from: [www.whatismyip.com](www.whatismyip.com), then get a friend to see if the page works for them or not ;).
- Josh

---

### Post by sabitha on 2006-10-03
> **firefly2442 said:**
> Try going to the terminal and typing "ifconfig".  This will tell you your IP address.  Like JamesVeDe stated, private IPs usually start with 192.X.X.X

127.0.0.1 is considered your "localhost" or local machine IP address.  Make sure it's not using this one because then only you will be able to see your website. :D

unfortunately i dont have it :( 
here's my ifconfig 
> eth0      Link encap:Ethernet  HWaddr 00:14:2A:82:36:55
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:678925 errors:0 dropped:0 overruns:0 frame:1064
          TX packets:586838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:427903090 (408.0 MiB)  TX bytes:106785781 (101.8 MiB)
          Interrupt:185 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:174764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:113063687 (107.8 MiB)  TX bytes:113063687 (107.8 MiB)

---

### Post by az on 2006-10-03
> **sabitha said:**
> just newbie question : 
how do i know local IP and public IP ?

Your router is supposed to be the dynamic dns client, not the box behind it.

See here:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

and here:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by splendid on 2006-10-05
Looks like I have a problem

eth0      Link encap:Ethernet  HWaddr 00:13:D4:11:08:B8
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe11:8b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1655 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1342691 (1.2 MiB)  TX bytes:1407371 (1.3 MiB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1804699 (1.7 MiB)  TX bytes:1804699 (1.7 MiB)


I installed dd client.

What should I do next?

---

### Post by splendid on 2006-10-07
I forgot to mention.  I have SSH and FTP working.  Both can be accessed by using either IP or URL.

Thanks for your Help!

---

### Post by splendid on 2006-10-11
I am able to access via Local Host.  DynDns is working because FTP and SSH are working.  Any idea on where the problem could lie?  I have port 80 open up on the router.

---

### Post by halitech on 2006-10-11
have you tried restarting apache?

---

### Post by splendid on 2006-10-13
I am thinking the problem is from something getting blocked.  Does anyone know if Comcast blocks port 80?

---

### Post by splendid on 2006-10-13
restarting apache did not work.  Wondering if Comcast blocks port 80.  The problem must either be a setting in my router, or a configuration in Apache.

---

### Post by halitech on 2006-10-13
if you set apache to listen on port 8080 and forward that port, does it work? I believe I heard comcast does block port 80 now tha tyou mention it

---

### Post by splendid on 2006-10-13
should the private ip for port 8080 be my local ip name 192.168.  or should it be the one I have setup with DynDns?

---

### Post by halitech on 2006-10-13
I set mine up in the dmz and nothing is blocked so maybe check out here

[http://www.portforward.com/routers.htm]("http://www.portforward.com/routers.htm")

for better info

---

### Post by halitech on 2006-10-13
also, try running the shields up rfom grc.com

[http://www.grc.com]("http://www.grc.com")

to see if things are going through

---

### Post by splendid on 2006-10-13
Visited the site, can you post link to the document you are talking about.  I did not see anything for DMZ.

---

### Post by halitech on 2006-10-13
you have to select your router first and it should give you info on setting it up

---

### Post by splendid on 2006-10-16
Halitech, Thanks for all your help!  I really appreciate it.  Everything is working fine.  I configured my router for port 8080, and can access the webpage using my URL with DynDns now.  

Any suggestions on the best way to upgrade to the lates version?  I am running version 5.10  Last time I tried to upgrade it messed up my system, and I had to start from scratch.

---

### Post by halitech on 2006-10-16
glad that it is working for you so guess we know the answer to comcast blocking port 80 :)

far as upgrading, do you mean upgrading Ubuntu to 6.06?

---

### Post by splendid on 2006-10-17
Yes, I was looking to potentially upgrade to 6.06 without undoing what I have setup on 5.10.  Last time I tried, it was real messy.

---

