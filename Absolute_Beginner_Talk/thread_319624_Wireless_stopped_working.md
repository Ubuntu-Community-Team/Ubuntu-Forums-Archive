---
title: "Wireless stopped working"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by benjjo on 2006-12-15
Hi, 1st time ubuntu install.
yesterday i installed 6.10 XUbuntu on my laptop (because it came with my magazine and ive been curious about Ubuntu for some time now)-
-Compaq
-Presario V2000
-Sempron +3000
Everything was going fine until mid night. My internet stopped working. Im using a wireless card-
-Dlink DWL-G630 
It was all sweet for about 5 hrs until midnight last night.
My ISP runs DHCP and that changes at mid night so im thinking that could be the problem (can dhcp upset the wireless configuration??)
Secondly, i have two two wireless routers in the house and for the first time i tried to connect to the second (which happens to have a spk) router at midnight so maybe THAT is the problem. But now i cant connect to anything accept Etho cable.
The card works fine on the XP partition. 
I'm using Wifi radar and im a little uncertain as how to 
configure it. Is there a walk through available? I seem to be going around in circles with google.
Any help would be appreciated (links whatever). Thanx in advance.

Oh and this whole Ubuntu thing is pretty cool. Never sused an operating system that was so easy to install!

---

### Post by benjjo on 2006-12-24
Ok, i think i worked it out.
Since i posted this thread i've re-installed ubuntu. This time with Dapper 6.06LTS. 
The problem i think was the driver for my wireless card. I found that on the second install, when i tried to search for other wireless points, my software (WiFi radar) would only find one point. I'm in the process of ungrading my Kernel so that i can install ndiswrapper (card driver) and subsequently install GTK-WIfi (another wireless manager).
In theory, having all of the latter configured, i can manage more than one wireless point.
Fingers crossed.
If anyone can see that im wasting my time, i would appreciate any comments.

---

