---
title: "New to Ubuntu, need help connecting to internet"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Vorteilspreis on 2008-04-03
Hello. I'm new to Ubuntu and I need help connecting to the internet. I haven't installed Ubuntu yet, I have just tinkered around with it for a few minutes and have tried to connect to the internet with no luck. I use a DSL modem and I am using a Compaq Presario SR5210NX PC.



In case this helps you guys here is a link to my PC and it's specs:

[http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12132708-12133156-78308260-78308260-78308260-80627243-81049497.html](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12132708-12133156-78308260-78308260-78308260-80627243-81049497.html)

---

### Post by ghost_ryder35 on 2008-04-03
u trying wirelessly or wired?
post 
```

lspci

```

---

### Post by crashcoredump on 2008-04-03
Does the install see your network adapter?
Have you run LiveCD and can you access the internet then?

at the command try 
```

$ sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1D:60:AB:2D:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1C:F0:9F:22:29  
       **   inet addr:10.128.42.9**  Bcast:10.128.42.15  Mask:255.255.255.240
          inet6 addr: fe80::21c:f0ff:fe9f:2229/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1363959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4678695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:433329964 (413.2 MB)  TX bytes:2233329272 (2.0 GB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45144 (44.0 KB)  TX bytes:45144 (44.0 KB)

```

Look for your IP , maybe something like 192.168.1.2 depending on your DSL config. Should just work.

if there is an issue where the card was not detected at boot try to restart the service with 

$ sudo service network restart

Let me know how that goes..


Boa Sorte

---

### Post by Vorteilspreis on 2008-04-04
> **crashcoredump said:**
> Does the install see your network adapter?
Have you run LiveCD and can you access the internet then?

at the command try 
```

$ sudo ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1D:60:AB:2D:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1C:F0:9F:22:29  
       **   inet addr:10.128.42.9**  Bcast:10.128.42.15  Mask:255.255.255.240
          inet6 addr: fe80::21c:f0ff:fe9f:2229/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1363959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4678695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:433329964 (413.2 MB)  TX bytes:2233329272 (2.0 GB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45144 (44.0 KB)  TX bytes:45144 (44.0 KB)

```

Look for your IP , maybe something like 192.168.1.2 depending on your DSL config. Should just work.

if there is an issue where the card was not detected at boot try to restart the service with 

$ sudo service network restart

Let me know how that goes..


Boa Sorte

Yeah, the install detects my network adapter properly. Will I need to type that code in somewhere? Sorry, but I don't know ANYTHING about Linux since I've only used Windows up until now. Can I somehow get to a screen that will allow me to enter my ISP's username and password? I'm on wired broadband.

---

### Post by drascus on 2008-04-04
well if your card is working properly then there should be an icon in the top right of the panel that is a networking icon. when you click on it, it should list the wireless networks in your area. If it doesn't work then go to applications->accessories->terminal then you can type the commands the other users suggested in the terminal window and see the output. there is great information for learning the basics of using linux in the help menu which is the blue question mark in the top panel go through their new to ubuntu tutorial.

---

### Post by Vorteilspreis on 2008-04-04
Here's the message I get when I filled in my ISP username and password, I don't know if this is the right place to set up your DSL connection but anyways, here's the screenshot:

[IMG]http://i78.photobucket.com/albums/j81/pat666rick/Screenshot.png[/IMG]

---

### Post by drascus on 2008-04-04
with wired DSL plugging in the computer to the modem should be all you need to do it should configure the network automatically. if it doesn't try unplugging the cable and pluggin it back in and just restarting back into ubuntu with the cable plugged in. It should just work with out any configuration.

---

### Post by Vorteilspreis on 2008-04-04
> **drascus said:**
> with wired DSL plugging in the computer to the modem should be all you need to do it should configure the network automatically. if it doesn't try unplugging the cable and pluggin it back in and just restarting back into ubuntu with the cable plugged in. It should just work with out any configuration.

How would it though? It would surely need to know your ISP details wouldn't it? How else could it connect to your ISP?

---

### Post by drascus on 2008-04-04
well I suppose it depends on your provider. most DSL providers assume that their customers will use wireless routers and or more then one computer. So they don't require static IP adresses. They usually use a form of dynamic IP assigning that allows for multiple computers to use the same router. So in other words you shouldn't need to enter that kind of information. Unless of course you have a service provider that requires a static IP adress, in this case go to ->system->administration->Network here click on wired network uncheck the roaming mode and enter you network details.

---

### Post by Vorteilspreis on 2008-04-04
> **drascus said:**
> well I suppose it depends on your provider. most DSL providers assume that their customers will use wireless routers and or more then one computer. So they don't require static IP adresses. They usually use a form of dynamic IP assigning that allows for multiple computers to use the same router. So in other words you shouldn't need to enter that kind of information. Unless of course you have a service provider that requires a static IP adress, in this case go to ->system->administration->Network here click on wired network uncheck the roaming mode and enter you network details.

BTW, I don't use a router and I don't use wireless.

---

### Post by Vorteilspreis on 2008-04-04
Just to let you guys know I HAVE NOT installed ubuntu yet, I am just running it off the livecd.

This might help you guys figure out my problem: My DSL connection doesn't use a router, it doesn't need software to work in windows and it isn't a USB type modem.

---

