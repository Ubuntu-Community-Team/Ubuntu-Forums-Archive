---
title: "[SOLVED] Sever Problems!!! Please Help!!!!!"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-28
Ok, so I have LAMP server installed. And my site runs off of phpBB. And I just got all this set up last night. And it was working AMAZINGLY! But now when I try to go to my site it ask for my routers information and crap?? It's set to dynamic ip that might be my problem? but when i tried to set it to static it totally messed up for a little bit but i fixed it. Please someone help. I have to get this site back up and running!

---

### Post by UltraMathMan on 2008-01-28
Do you have port forarding for Apache set up in the router? I've never done the LAMP thing personally, but it looks like the connection is stopping at the router.

-Hope this helps :)

---

### Post by RadiationHazard on 2008-01-28
yeah. i'm pretty sure. cuz it was working perfect before! and now it's stopped working.

---

### Post by emarkd on 2008-01-28
Are you running that browser on the same computer that the server is running on?  If so, try accessing your site by just going to [http://localhost](http://localhost).  If that works, your problem is not with your server but probably lies with your router.  I'd restart the router and see if it straighten out.

---

### Post by UltraMathMan on 2008-01-28
Right, but if the server had a dynamic IP and that changed, the router wouldn't be able to find the server at the old address to forward the request to Apache.

---

### Post by emarkd on 2008-01-28
UltraMathMan is correct.  You should set your router up to always give the same static IP to your server box and then forward port 80 to that private IP.

---

### Post by RadiationHazard on 2008-01-28
[http://localhost/]("http://localhost/") works just like it should. so please step by step what should i do to fix my problem? :confused:

---

### Post by emarkd on 2008-01-28
The problem is with your router and every router's interface is different.  See if you can tell how to set your router to assign a static IP to your server.  Then set up your router to do port forwarding and forward 80 to that same IP

---

### Post by UltraMathMan on 2008-01-28
You're going to need to log into the router and go to the [port forwarding page]("http://portforward.com/english/routers/port_forwarding/Netgear/WGR614v7/VNC.htm") and add port 80 with the server's current IP. To check on the server do ```
ifconfig
```.

---

### Post by RadiationHazard on 2008-01-28
this is what came up when i put that command in.

```
jordan@jordan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:A9:80:D7:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:31:A2:43  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe31:a243/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13815 errors:11 dropped:210 overruns:0 frame:0
          TX packets:14238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14094510 (13.4 MB)  TX bytes:5105902 (4.8 MB)
          Interrupt:18 Base address:0xe000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:238936 (233.3 KB)  TX bytes:238936 (233.3 KB)

jordan@jordan-laptop:~$ 
```

---

### Post by UltraMathMan on 2008-01-28
So I'm assuming you gave the server a static IP of 192.168.1.4, correct? if so that's the IP you need to point the port to in the router.

---

### Post by Dr Small on 2008-01-28
If you would like detailed instructions that match your router's make and model, then stop on over at PortForward.com and find your router:
[http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm)

Dr Small

---

### Post by RadiationHazard on 2008-01-28
thank you! the problem is solved for now!!:)

---

### Post by UltraMathMan on 2008-01-28
Glad to help :)

---

