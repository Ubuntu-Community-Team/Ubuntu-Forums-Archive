---
title: "Cannot connect to the internet"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Wally Paulnuts on 2007-06-13
Hey everyone, i have been reading the posts and the manual online but I am unable to connect to the internet after installing Ubuntu. Let me give a little background if it helps, I have Verizon Fios Service and I am connecting through an Actiontec router. I am currently writing this post from my Dell laptop running XP through the hard wired connection no problem. I have been trying to connect by taking the Ethernet cable out of the laptop and into my desktop (small pizza box style Compaq deskpro P3 866mhz 512mb with the on board Ethernet port which is funtional). I have set a static IP for the deskpro which is running ubuntu at 192.168.1.15...I am getting no connection to the internet at all, I am totally lost as to how to proceed. Any help would be appreciated....I can post anything from the gnome terminal here in future posts if that could be of use. 

thanks

wally Paulnuts :(

---

### Post by charles.g.moore on 2007-06-13
could you post your ifconfig -a

also, are you able to ping the router?

---

### Post by neorou on 2007-06-13
Do you have the live CD? Did you try booting from it and trying to connect? Maybe you have a hardware issue.

---

### Post by Wally Paulnuts on 2007-06-13
ok here is my ifonfig - a results

eth0      Link encap:Ethernet  HWaddr 00:02:A5:1E:CC:95  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fe1e:cc95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59140 (57.7 KiB)  TX bytes:59140 (57.7 KiB)


I am unable to Ping the router, the destination is unreachable. all the hardware was working previously with windows xp so i know that the hardware is not the issue. thanks again guys let me know if there is more info needed.

---

### Post by irish_flu on 2007-06-13
Any chance that the static IP you're using isn't a valid choice (as far as the router is concerned), or that the router is incorrectly entered in your config??

---

### Post by Wally Paulnuts on 2007-06-13
<<<Any chance that the static IP you're using isn't a valid choice (as far as the router is concerned), or that the router is incorrectly entered in your config??>>>

It is a clear IP there are no other conflicts with that address on the network; how do i know if the router is incorrectly entered in my config?

---

### Post by Austin_KW on 2007-06-13
What is the ip on the working windows PC. ipconfig/all
Are you sure that you are not on 192.168.0 subnet

---

### Post by irish_flu on 2007-06-13
> **Wally Paulnuts said:**
> 
It is a clear IP there are no other conflicts with that address on the network; how do i know if the router is incorrectly entered in my config?

I'm sure you probably have your stuff together, I just wondered if there was a typo in the "gateway address" listed for your router in Network Settings (the same place you probably entered your IP and such).  Not that you would do that, but sometimes I'll work on stuff forever only to find it was something very simple.  :)

---

### Post by ajskhan on 2007-06-13
> **Wally Paulnuts said:**
> Hey everyone, i have been reading the posts and the manual online but I am unable to connect to the internet after installing Ubuntu. Let me give a little background if it helps, I have Verizon Fios Service and I am connecting through an Actiontec router. I am currently writing this post from my Dell laptop running XP through the hard wired connection no problem. I have been trying to connect by taking the Ethernet cable out of the laptop and into my desktop (small pizza box style Compaq deskpro P3 866mhz 512mb with the on board Ethernet port which is funtional). I have set a static IP for the deskpro which is running ubuntu at 192.168.1.15...I am getting no connection to the internet at all, I am totally lost as to how to proceed. Any help would be appreciated....I can post anything from the gnome terminal here in future posts if that could be of use. 

thanks

wally Paulnuts :(
I had THIS EXACT SAME SETUP except with diff pc's. Vzon Fios, actiontec router. I could not get the wire to work no matter what settings. If anyone gets this to work please please alert me - by Pm if possible!

---

### Post by irish_flu on 2007-06-13
One other thing that can be easily overlooked; in "Network Settings", make sure the box next to your ethernet connection is checked (which enables the connection).  You can still configure it and retrieve settings from ifconfig even if it's disabled, IIRC.

---

### Post by Wally Paulnuts on 2007-06-13
the ip on my working dell window based laptop is 192.168.1.8 ; on the Ubuntu Desktop the ip and gateway are in the right places (gateway is 255.255.255.0) and the check box is checked. i wonder if these actiontec routers are the problem, i am having wireless connectivity issues with it also but the hardwired connections work 100% fine......

---

### Post by Wally Paulnuts on 2007-06-13
Anyone have any thoughts after seeing my ifconfig -a results?

---

### Post by LAZER61 on 2007-06-30
My book says to uncheck the box then check it again.  It worked for me.

---

