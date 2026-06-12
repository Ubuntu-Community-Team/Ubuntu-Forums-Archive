---
title: "[SOLVED] unable to connect to net"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by tollboy on 2007-12-03
plzzzzzz
help me i had installed ubuntu yesterday and i am nt able to connect to net till now 
when i tried if config then output is given in screenshot
i attached with this 
and pppoe config is not working 
i tried pinging too bt it saying host unreachable plz helppppp

---

### Post by lvleph on 2007-12-03
Are you kidding with posting this more than once? How about a little patience!

[It was just 18mins ago that you posted this.](http://ubuntuforums.org/showthread.php?t=630424)

[url=http://ubuntuforums.org/showthread.php?t=629686]And make that more than once before.

In fact this one has an answer to help you.[/url]

> **daimaru said:**
> i really dont know why i m posting this since you dont seem to read the posts. but here it goes
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

### Post by tollboy on 2007-12-03
i am sorry for that bt what can i do 
my fingers r digging in my palm just to connect with net
i have to try the advise by rebooting my system to ubuntu and then again answering
it the post by rebooting to windows.
i am doing this from last night 
hw much i have to keep patience

---

### Post by tollboy on 2007-12-03
nothing is working will any tell me in some more detail
pleasssssseeeeeeeeee

---

### Post by daimaru on 2007-12-04
@tollboy 
hi there. i'm not quite sure where to post since you have 2 threads running on this subject, but i'll give this one a try. (please close one of the threads)
before anyone here can help you with your connection problem they will need to know a few things.

are you trying to connect via wireless or LAN or modem ? 
meaning are you trying to connect with a modem (the old baud type connection) or do you have a ethernet connection ( ethernet cable that goes directly from your laptop to your DSL modem or router) or are you connecting wirelessly?

please post the output of the following command as an attachment to your next post.

```
 sudo lshw > hardware.txt
```
this creates a hardware.txt file in your working directory which you can then attach to your next post.

your ifconfig looks kind of weird what is that eth2 stuff doing there? . 
if your using wireless post the iwconfig output too. 

sry can't be of more help right now.

---

### Post by tollboy on 2007-12-23
thanks friend 
i rinstalled ubuntu uninstalling my windows vista 
ang this time i used GUI to connect to internet
and it is going well till now 
well i have dual boot system coz i have open suse too
bt i mostly used ubuntu for it simply city 
thanx once more

---

