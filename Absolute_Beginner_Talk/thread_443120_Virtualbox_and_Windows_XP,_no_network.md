---
title: "Virtualbox and Windows XP, no network"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by NikoC on 2007-05-14
In our lab I need a few Windows XP applications like FileMaker, Graphpad and Sigmaplot... so I decided to install Windows XP via Virtualbox (also tried VMWare, but via Virtualbox things work faster for me). 
Now when I fire up XP everything works just fine, nice quick 'virtual' bootup... I can even open websites using explorer.... however I'm unable to ping or access the lab's server via the virtual XP! Any idea what's going wrong?

I'm using Feisty (since development release Herd 3), latest Virtualbox release as a .deb package for Ubuntu Feisty, Network settings in Virtualbox use NAT and a generated MAC address (changing the MAC address to the one I get from ifconfig eth0 doesn't change a thing btw).

---

### Post by ghostborg on 2007-05-14
I am using ubuntu 7.04 and Virtualbox Windows XP as guest.
I had Internet "out of the box" but could not browse my lan.
After following the instructions I noticed that while I was running WinXP I could
not use the internet under linux at the same time. After closing my WinXP session
Linux internet and browsing returned to normal. I guess Virtualbox takes total control
of the network card after following the link below.

Hope this helps

I followed the instructions at the link below under the heading of  Networking.

[URL="http://doc.gwos.org/index.php/VirtualBox#Networking"]

---

### Post by NikoC on 2007-05-15
Hmmz thanks for the reply, going to try that out tomorrow since I had classes all day and did not have access to my ubuntu lappy.

---

