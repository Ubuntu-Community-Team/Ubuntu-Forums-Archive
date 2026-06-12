---
title: "How to get the net working"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Respenus on 2007-03-16
Some time ago, I came to this forums, trying to find out, which Ubuntu to install. Server or desktop one on the school computer.

Based on the answers I have been given I have decided to try the server install. Because I knew I would face difficulties with the installation, as I am a complete noob to configuration.

But every single tutorial was based on the DHCP on the install working. Because I tried once before and have seen the DHCP didn't automaticly setup. So I wrote down every single configuration I could find (which I knew of, later on I found I forgot "interfaces").

So during install I opted for a manual config of the network and used the previously used settings. It installed nicely, but the net isn't working. Because I don't know much, I don't even know whta could be wrong. I tried to use PuTTY, but if faled to login, most probably due t the lack of knowledge on my part.

It's a school computer, on an networked connection.

If you havy any idea on how to continue, I would be very grateful if you did so and any other suggestions you may have for me, would also be very nice.

I'm most probably going to install the desktop version, just to have a GUI to work from.

Thank you in advance.

---

### Post by schwascore on 2007-03-16
Since it is on a school network, you should ask a school admin if DHCP is enabled or if each computer has a static IP address.  Regardless, you should tell the admin what you are trying to do and get the following information:

- is DHCP enabled.
- the address of the gateway (router).
- netmask.
- static ip you could use if they do not have DHCP enabled.
- DNS servers.  You can always use OpenDNS servers which are 208.67.222.222 and 208.67.220.220.

You should be able to manually configure the network with that information, but your success might also depend on the security measures taken by you school.  If they filter based on IP or MAC address, you'll have to get help from an admin.

---

### Post by Respenus on 2007-03-16
Thank you. So talking with the admin it is. If I remember correctly, the system was set at a static IP.

But I have all the info needed, is there anywhere I should specificaly look to check if "they are there"? It's possible that the manual config didn't ask me for all the info :confused: Hell, what the heck to I know about Linux :(

---

### Post by Respenus on 2007-03-18
*bump* 

I'm not usualy a person who does such things, but I would like where do I need to set the internet connection and any other help you can offer on the subject (so that I don't stop with every step).

Thank you.

---

### Post by Respenus on 2007-03-19
I have some new info, that will help me (us) figure this out.

I have rechacked interfaces and made sure, I put in all the "previous" info. Still, it doesn't work.

But I can ping the linux computer from another school computer, but I can't ping the school computer from the Linux machine. So its an outgoing problem, not incoming.

I hope this will help you guys.

---

### Post by Respenus on 2007-03-19
*bump* Anyone?

---

### Post by mendingo84 on 2007-03-19
ask your administrator if you go through a proxy. if yes, set it up.

---

### Post by Respenus on 2007-03-19
> **mendingo84 said:**
> ask your administrator if you go through a proxy. if yes, set it up.

As a noob I must ask questions.

Where? I must be spoon feed, although you may not like, I may not like it, but we both have to do it.

Thank you anyway!

---

### Post by thomas576 on 2007-03-19
im new here to but heres what i know, open up a term window or if you dont' have xwindows running even easier, but the first device in your system for the network card should be eth0 or 1 i think i have 2 net connections on my puter *not sure,  so type the following and look for the stuff after it and see if you have what i have (of course the address will be different and im on dhcp but we can walk this though)

at prompt do

ifconfig

my output is 
eth1   Link encap:Ethernet  HWaddr 00:11:2F:32:1B:4D  
          inet6 addr: fe80::211:2fff:fe32:1b4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17191618 (16.3 MiB)  TX bytes:5741477 (5.4 MiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160131 (156.3 KiB)  TX bytes:160131 (156.3 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:169.161.231.34  P-t-P:69.130.64.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:22173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:16561689 (15.7 MiB)  TX bytes:5119821 (4.8 MiB)

now of course i have a ppp0 connection cuz im on a dsl line and not a regular network  but i would expect to see the eth0 or 1 config ready do go

also the lo divice is called your loopback device and should be 127.0.0.1 and you should be able to ping this from your linux machine (it just bounces packets back to you)
hope this is a start
thomas

---

### Post by zvacet on 2007-03-19
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")

---

### Post by Respenus on 2007-03-20
Thank you thomas576.

Zvacet, I already know that tutorial. I don't want to sound cocky, but if you read it, you would see, it works on the principle that the DHCP config is done automaticly, not manualy, which is my case.

---

### Post by Respenus on 2007-03-20
> **thomas576 said:**
> im new here to but heres what i know, open up a term window or if you dont' have xwindows running even easier, but the first device in your system for the network card should be eth0 or 1 i think i have 2 net connections on my puter *not sure,  so type the following and look for the stuff after it and see if you have what i have (of course the address will be different and im on dhcp but we can walk this though)

at prompt do

ifconfig

my output is 
eth1   Link encap:Ethernet  HWaddr 00:11:2F:32:1B:4D  
          inet6 addr: fe80::211:2fff:fe32:1b4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17191618 (16.3 MiB)  TX bytes:5741477 (5.4 MiB)
          Interrupt:209 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160131 (156.3 KiB)  TX bytes:160131 (156.3 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:169.161.231.34  P-t-P:69.130.64.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:22173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20636 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:16561689 (15.7 MiB)  TX bytes:5119821 (4.8 MiB)

now of course i have a ppp0 connection cuz im on a dsl line and not a regular network  but i would expect to see the eth0 or 1 config ready do go

also the lo divice is called your loopback device and should be 127.0.0.1 and you should be able to ping this from your linux machine (it just bounces packets back to you)
hope this is a start
thomas

Thanks. Not too much help, but I did manage to ping the loopback device. Not that it means anything. or does it...?

---

