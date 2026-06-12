---
title: "I cannot access internet (except for Google)"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-05-18
This is a weird problem.  When I log on Feisty (AMD64) will not find my wired connection if it is connected.  But if I log on with it disconnected and connect it after log on, Feisty will find it.  Even then I cannot access the internet.  However, I can type any search parameters into the search box and Google will come up with the appropriate results.  This is a new install so there are no cached pages.  None of the links work from the Google page except for the one that takes you to more search results.  If I change the DNS in /etc/resolv.conf to the one for FreeDNS, then I can't even access Google. PLEASE HELP!:confused:

---

### Post by Happy_Man on 2007-05-18
What's your ISP?

---

### Post by WhiteSphinx on 2007-05-18
My ISP is Qwest via a DSL connection with dynamic IP.  When I boot up in WinXP, I connect to the internet without a hitch - so it has nothing to do with the ISP.  It is an Ubuntu problem.

I must add that everything worked fine when I was using Edgy (except that I had to use FreeDNS).

---

### Post by zostra on 2007-05-18
new to ubuntu myself but i work for verizon dsl so i might be able to help.

are you able to ping different websites? or their ip addresses ?

:D zostra :D

---

### Post by WhiteSphinx on 2007-05-18
I don't know how to do this.  I am just an average Joe -- I am not a techie

---

### Post by zostra on 2007-05-18
in a terminal window type the following three commands

ifconfig

ping -c4  [www.yahoo.com](www.yahoo.com)

ping -c4 209.131.36.158

and tell me the results

:D zostra :D

---

### Post by WhiteSphinx on 2007-05-18
Okay, here are the results:

jennifer@jennifer-desktop:~$ ifconfig
eth0   Link encap:Ethernet  HWaddr 00:19:21:4A:F0:1E  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe4a:f01e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2551 (2.4 KiB)  TX bytes:5157 (5.0 KiB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

jennifer@jennifer-desktop:~$ ping -c4 [www.yahoo.com](www.yahoo.com)
PING [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) (209.131.36.158) 56(84) bytes of data.
64 bytes from [www.yahoo.com](www.yahoo.com) (209.131.36.158): icmp_seq=1 ttl=51 time=58.5 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.131.36.158): icmp_seq=2 ttl=53 time=57.2 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.131.36.158): icmp_seq=3 ttl=54 time=58.0 ms
64 bytes from [www.yahoo.com](www.yahoo.com) (209.131.36.158): icmp_seq=4 ttl=53 time=58.7 ms

--- [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 57.240/58.141/58.716/0.596 ms
jennifer@jennifer-desktop:~$ ping -c4 209.131.36.158
PING 209.131.36.158 (209.131.36.158) 56(84) bytes of data.
64 bytes from 209.131.36.158: icmp_seq=1 ttl=53 time=58.1 ms
64 bytes from 209.131.36.158: icmp_seq=2 ttl=51 time=58.2 ms
64 bytes from 209.131.36.158: icmp_seq=3 ttl=51 time=59.0 ms
64 bytes from 209.131.36.158: icmp_seq=4 ttl=51 time=58.2 ms

--- 209.131.36.158 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3010ms
rtt min/avg/max/mdev = 58.189/58.437/59.096/0.482 ms

---

### Post by zostra on 2007-05-18
there is no problem with your connection

what ever dns settings you have right now are working and yahoo is getting resolved to its ip and you are getting replies from it that means it is a browser issue.

which browser are you using?
try a different one.

:) zostra :)

---

### Post by xillimiandus on 2007-06-03
This thread and, in particular, this link, should help :
thread : [http://ubuntuforums.org/showthread.php?t=418144](http://ubuntuforums.org/showthread.php?t=418144)
link : [http://articles.techrepublic.com.com/5100-1035_11-6174075.html](http://articles.techrepublic.com.com/5100-1035_11-6174075.html)

---

### Post by WhiteSphinx on 2007-10-28
Okay this is too cool.  Problem solved.  This should work for anyone with an A33G PC Chips Motherboard or for anyone with an SiS190/191 ethernet.

First do this:

```
export EDITOR=gedit && sudo visudo
```

This will bring up the sudoers file.

Replace the following line (because of a bug)

> Defaults !lecture,tty_tickets,!fqdn

with:

> #Defaults !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"

Add this line to the end of the sudoers file:

> username ALL=NOPASSWD: /sbin/ifconfig
Be sure to replace "username" with your own username.

Then open System>Preference>Sessions

Click Add

_N_ame > Configure LAN
_C_ommand > sudo ifconfig eth0 mtu 1492

Now you will be able to access the internet with you SiS190 Ethernet after you restart.

---

