---
title: "just plain help"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Lisa Y on 2008-01-17
Hello everyone....i am absolutely lost in how to connect my Linux Version 7.10 (gutsy) to my network at home which is using the Linksys WRT54GS...now the thing is that i dont have a network card for this laptop but i use the wi-fi to connect to the router...now the catch is that the router is using a MAC-filter..now i know there is plenty information on connecting a network and i think ive read most of the things that people have provided can anyone provide an easy guide for idiots to get my wifi working correctly??

Thanks !

---

### Post by HermanAB on 2008-01-17
Well, if you are totally lost and looking for mouse clickety wizards, then you are using the wrong distribution.  You should install Mandriva Linux if you want a point and click system.  Mandriva has wizards for everything, including WiFi and ndiswrapper.  Ubuntu is for people who like to play on the command line.

Otherwise, I suggest that you first of all disable MAC, SSID and WEP crud on the WiFi access point and experiment in plain text till you got things working.  MAC and SSID filtering is just an inconvenience anyway and doesn't really do anything useful.

You most likely need to use the ndiswrapper system to load a MS Windows driver for your WiFi adaptor, unless you are so lucky as to have an Intel one.  See this: [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

Hope that helps!

Herman

---

### Post by EXCiD3 on 2008-01-17
What is the wireless card that you have?

---

### Post by Iowan on 2008-01-17
Welcome to Ubuntu... hopefully someone can help w/ your problem.   Is the laptop new to your net?  (Is it's MAC address in the router?)

Anything [HERE]("http://ubuntuforums.org/showthread.php?t=603154") useful?
[THIS]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads?action=fullsearch&context=180&value=wifi&titlesearch=Titles") is another one.

---

### Post by nikoPSK on 2008-01-17
> **Iowan said:**
> Welcome to Ubuntu... hopefully someone can help w/ your problem.   Is the laptop new to your net?  (Is it's MAC address in the router?)

I would suspect

---

### Post by TheNomad on 2008-01-17
Well, in order to gain access to this router, you need to go to a computer, which already has access to it and enter your wireless card's MAC address to the filtering page as one of the accepted addresses.

To find the mac address: 

Open a terminal window and at the command prompt, type :

ifconfig -a

you will see a screen output like this:

eth0      Link encap:Ethernet  HWaddr 00:02:A5:7C:A1:3C  
          inet addr:10.2.32.227  Bcast:10.2.32.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fe7c:a13c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1165 txqueuelen:1000 
          RX bytes:3416822 (3.2 MB)  TX bytes:493467 (481.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:600 (600.0 b)  TX bytes:600 (600.0 b)


there may be more than two blocks of information, which means you may have more than one network interface or if this is a workplace provided laptop, you may have IPSEC virtual interfaces installed, but one block you will need is the one pertaining to your wireless card's output. Since where I am writing this does not have a wireless card but a wired connection, I am going to use my eth0: block. MAC address you are looking for is the 6 hexadecimal digits on the same line as eth0. In my example, you are looking for:

HWaddr 00:02:A5:7C:A1:3C

note down these 6 hexadecimal numbers on a piece of paper and go to the computer with access to the wireless router, enter the administration page and find your way to the MAC filters page. Then enter this address and reboot the router if it is required by the configuration screen.

That should do it.

Hope it helps

---

### Post by hyper_ch on 2008-01-17
and use a DESCRIPTIVE TOPIC TITLE and not a genereic "noob here" or "need help"

---

### Post by Lisa Y on 2008-01-17
oh wow...THANK YOU so much for providing all these links for me!!! I didt think using linux would be such a change. but i do love the command line that i have to use. I guess this just takes some time getting use to. I have managed to install wifi-radar...but not my home network ( how embarrassing  )

Still in the process of reading the information that has been provided to me. But at the moment i have added my MAC address to my MAC filter using the "ifconfig -a" prompt. 

since i dont have an adapter for my wifi on the other hand it is integrated wifi with the laptop here. Would it make any difference to the information that was provided to me here?

---

### Post by Iowan on 2008-01-17
The information presented should be accurate for on-board (integrated) wi-fi or add-on card.  Command line is FUN (actually preferred) once you get used to it.

---

### Post by nikoPSK on 2008-01-17
> **Lisa Y said:**
> oh wow...THANK YOU so much for providing all these links for me!!! I didt think using linux would be such a change. but i do love the command line that i have to use. I guess this just takes some time getting use to. I have managed to install wifi-radar...but not my home network ( how embarrassing  )

Still in the process of reading the information that has been provided to me. But at the moment i have added my MAC address to my MAC filter using the "ifconfig -a" prompt. 

since i dont have an adapter for my wifi on the other hand it is integrated wifi with the laptop here. Would it make any difference to the information that was provided to me here?

command is fun. Problem solved? Please goto the top of the page, above the first post of the page, thread tools, mark this thread as "SOLVED". :)

nikoPSK

---

### Post by hyper_ch on 2008-01-17
if you want to get started on the command line, have a look at:

[http://www.linuxcommand.org](http://www.linuxcommand.org)

Also search for the us La Roza - in his signature there are also a few links for that.

---

