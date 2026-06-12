---
title: "wireless stops working on re-boot"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by oisuxx on 2007-12-17
hi all....
ive been fiddling with ubuntu 7.10 for about 2 weeks now. i have a problem with my internet wireless card....

when i start ANY flavor of ubuntu (im on the live boot cd of xubuntu now posting this) my wireless card is found, and connected to with WEP...
when i restart my computer (i tried to install samba for my xbox media center) it looses visibillity of the wireless. can anyone help me out. im not familliar with the commands. i see alot of people saying "type sudo /blah blah" but im not that savvy yet. 

can someone give me a step by step on why this is happening. and how to fix it please?

---

### Post by brunetteredhead on 2007-12-17
When you say it loses visibility of the wireless, what do you mean?  It doesn't detect any wireless access points available, or that it doesn't connect?

Also, if you could issue an "ifconfig" command and show me the output, I might be able to help you a little bit more.  The ifconfig command is very similar to the ipconfig command on a windows machine if you have ever used it- it shows detailed connection info on each of your network ports.

---

### Post by oisuxx on 2007-12-17
well when i run this Xubuntu live boot cd. i can see all the wireless networks in my area. i connect to mine. and now im online. same with when i ran the live boot for regular ubuntu 7.10, it saw all the wireless networks. i installed it and everything was fine. untill i installed SAMBA and it asked me to restart, i did and now it dosnt see anything... there is no option for wireless networks anymore in the program that it finds wireless connections, only a wired connection....and even then it wont connect, i tried dhcp and roaming, but it wont connect to my onboard lan. so i bought a belkin, same thing....nothing. so then i bought this USB linksys adapter....still nothing, im getting very frustrated, becuase all the howto's i find you need a connection to download all these packages and such.


this is what i get with ifconfig

ubuntu@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:14:78:72:EE:48  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe72:ee48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50013473 (47.6 MB)  TX bytes:2434875 (2.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:11:5B:01:BF:C6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-14-78-72-EE-48-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:281486 errors:0 dropped:0 overruns:0 frame:52385
          TX packets:24199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:79782658 (76.0 MB)  TX bytes:3203957 (3.0 MB)
          Interrupt:20 

ubuntu@ubuntu:~$ 

again keep in mind that im running this live boot cd atm and not my regular ubuntu on my harddrive. when i take this live boot cd out and load up my regular 7.10 it wont see anything, so i dont know if the settings would be the same.

any help or a step by step would be awesome (im only about 3 weeks in with ubuntu and linux)! thanks for the reply!

---

