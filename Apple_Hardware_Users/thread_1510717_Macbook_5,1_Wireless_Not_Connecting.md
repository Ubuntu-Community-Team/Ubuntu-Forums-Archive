---
title: "Macbook 5,1 Wireless Not Connecting"
date: 2010-06-15
forum: Apple Hardware Users
---

### Post by TrendyGuy on 2010-06-15
Hello all,

I am a first time linux user and have recently decided to start booting Ubuntu on my Macbook 5,1 to try it out and learn something new. I had absolutely no problem installing, everything worked great just following instructions I read online. My first hurdle is to get my wireless working though. The first thing I did was go to the help section of Ubuntu but that seems to only help you if you are already online or have your wireless card working already. Next I looked online/forums and found that I needed to install the correct drivers so I installed:

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)
[http://packages.ubuntu.com/karmic/dkms](http://packages.ubuntu.com/karmic/dkms)
[http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)

When I rebooted my wireless is finding all the local networks. I tried to connect to mine and nothing happens at all. It just keeps trying to connect to it but it never does. I even tried to connect to a completely open wireless network with no security and it still did not work. From here I am not sure what to do. I am willing to try any recommendations. Thank you in advance for any help.

---

### Post by Ravernomina on 2010-06-16
> **TrendyGuy said:**
> Hello all,

I am a first time linux user and have recently decided to start booting Ubuntu on my Macbook 5,1 to try it out and learn something new. I had absolutely no problem installing, everything worked great just following instructions I read online. My first hurdle is to get my wireless working though. The first thing I did was go to the help section of Ubuntu but that seems to only help you if you are already online or have your wireless card working already. Next I looked online/forums and found that I needed to install the correct drivers so I installed:

[http://packages.ubuntu.com/karmic/patch](http://packages.ubuntu.com/karmic/patch)
[http://packages.ubuntu.com/karmic/dkms](http://packages.ubuntu.com/karmic/dkms)
[http://packages.ubuntu.com/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/karmic/bcmwl-kernel-source)

When I rebooted my wireless is finding all the local networks. I tried to connect to mine and nothing happens at all. It just keeps trying to connect to it but it never does. I even tried to connect to a completely open wireless network with no security and it still did not work. From here I am not sure what to do. I am willing to try any recommendations. Thank you in advance for any help.

i Think you installed the "free" drivers which do not work on Newer Mac Models. Your going to want to install the Broadcom STA drivers. You Wireless card manufacture Made them so there going to work without a doubt. Install it from System>Admin>Hardware drivers. You will need an internet connection to download them. So plug your computer directly into the Modem. (The cord from the back of the wireless router that leads to the modem.) Download install then reboot. GL :D btw welcome to the forums :3

---

### Post by naturista futurista on 2010-07-06
Hi all!

I also have got a Macbook 5,1, but running Lucid Lynx, and have exactly the same problem. I can't find the way of fixing it.

I installed the proprietary Broadcom STA drivers but they don't seem to work. I can see the network but it seems to be impossible to connect to it. I tried wicd but everytime it says 'Bad Password' even if the network is completely open.

Hope someone has an idea! Thanks a lot!

Big hug,

Christian

---

