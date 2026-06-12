---
title: "Synaptic and weather applet not working."
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by corstar on 2005-10-16
[CENTER][COLOR=Red]**_[B]SOMEONE PLEASE HELP**_[/B][/COLOR][/CENTER]
 I have posted a few times on this subject and have had less than a handful of responses. I have found there are alot of issues being solved, But none in my posts.

[COLOR=Red]Am I asking the wrong questions, are the answers blatently obvious to everyone but me?[/COLOR]

Someone please help me here!!! It's realy getting to me now. If I can't resolve it soon, I will have to go back to using fc4, but don't want to because my wireless works in 5.10 and I want to learn so I can help others in the future.:(  without apt I'm pretty screwed.

Right, [COLOR=black]**[COLOR=black][COLOR=Red]The problems[/COLOR][/COLOR]**[/COLOR].............
1/ Synaptic or Apt does not work.  I have tried every combination of repos possible, but get a "failed" every single time. 

2/ The weather applet does not work either. It used to under 5.04

3/ I have never been able to send/recieve email in a client under linux, but web based works fine.

I am running behind a DLink G604T router. I have switched off all the firewalls, put this computer in the "DMZ" (de-militarized zone - no port blocking) 
I have tried having every single port open through the firmware.

I notice that when I try to download an autopackage,the script seems to want to get it from router address 10.0.0.0. But I know for a fact, my router address is 10.1.1.1 and my laptop number is 10.1.1.3. Could this possibly be the cause of all evil on my machine??

Finaly what diagnostic outputs would you like to get me on my way.
(here is my ifconfig)

[php]root@ubuntu:/home/corstar# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:71654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6503435 (6.2 MiB)  TX bytes:6503435 (6.2 MiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:5A:21:19
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::211:9ff:fe5a:2119/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:502 txqueuelen:1000
          RX bytes:42953712 (40.9 MiB)  TX bytes:3636369 (3.4 MiB)
          Interrupt:19 Base address:0x4000[/php]

---

### Post by Ampersand on 2005-10-16
Have you made sure your gateway settings are correct? In the System menu, go to Administration - Networking. Click on Ethernet connection, go to Properties, and make sure it's got the correct settings (or DHCP, if appropriate).

---

### Post by corstar on 2005-10-16
Yes, I've got DHCP selected. That seems to work fine for web browsing.
I'm not sure how to set up the specific ip information though.
Thanks for replying

---

