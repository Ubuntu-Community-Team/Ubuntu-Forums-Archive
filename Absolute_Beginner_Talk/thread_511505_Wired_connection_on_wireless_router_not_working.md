---
title: "Wired connection on wireless router not working"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by paker on 2007-07-27
I have been using D-link wired router under Feisty. I want to switch to wireless. First, I replaced the D-link wired router with US Robotics wireless router, but kept the wired connection. The "2 computer icon" at top right says I have a wired connection. But when I enter [http://www.xxx.xxx](http://www.xxx.xxx), I get "server not found."

I have read other threads here. They seem to indicate that routers are not OS specific. How can I troubleshoot? Thanks.

Feisty 32 bit,

---

### Post by KyleBrandt on 2007-07-27
Can you give a more clear description of what your set up looks like now?  Your feisty box is connected to which router currently, and how is it connected (Wire or wireless)?

Also, it might help if you open up the terminal, and paste your output from the command, "ifconfig"

---

### Post by paker on 2007-07-27
1) Right now, the computer is connected to D-link Wired. ifconfig generates the following:

rust@rust-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:46:0D:BC  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe46:dbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:337236 (329.3 KiB)  TX bytes:25486 (24.8 KiB)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

rust@rust-desktop:~$ 

2) I replaced D-link Wired router with US Robotics Wireless router. I used the same cables to connect computer to the Wireless router. I couldn't get internet.

In a while, I will replace D-link Wired with US Robotics Wireless, and run "ifconfig" and paste the outcome.

Thanks.

---

### Post by paker on 2007-07-27
I now have US Robotics Wireless Router. But the computer connection is still wired. I am writing this post with the US Robotics Wireless router. I don't really know why it didn't work then but is working now. The only thing I did differently was to turn off the cable modem briefly after switching the router. Maybe that solved the problem. Thank you for your help.

---

### Post by st33med on 2007-07-27
Whoops! Sorry, talking about something else.

---

