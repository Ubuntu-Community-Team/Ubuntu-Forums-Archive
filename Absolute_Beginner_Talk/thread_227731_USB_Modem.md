---
title: "USB Modem"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Skyrail on 2006-08-02
USB modem, I have had a look around the web, and the website doesn't provide any drivers for the modem (on linux that is). So is there any easy way to configure it so I can use it? At the moment I don't want to spend any money on a router but by the sounds of thigns it looks like I'm going to have to. The modem is a ZyXEL Prestige 630-C1 series modem, if I can't get that working, how much would a cheap yet reliable router cost? And how easy would that me to use to conenct to the itnernet? Is that Plug in and go?

---

### Post by soul_rebel on 2006-08-02
please post the output of 
sudo lsusb
There are two different zyxel 630 models. They both can work with linux

---

### Post by anaconda on 2006-08-02
Knoppix regognized my USB modem without problems, Havent tried it in ubuntu, because Now I have a new adsl-modem..

about 1 year ago I paid 38$ for a cheap external router/firewall/ADSL-modem,  which is connected to an ethernet-card.. (I can connect up to 4 computers to this modem)

Now it would probaply be a bit cheaper.

After buying this I havent had any problems. All operating systems I have tried regognize my ethernet card without problems, and that is enough to make the internet connection work... So no need to regognize the adsl-modem. as long as the ethernet card is regognized.. 

It is also really nice to have a hardware firewall.. before that I had some problems with windows, when the software firewall didn't start once, and I had to reistall windoze.. I reason, more to move to linux.

---

### Post by anaconda on 2006-08-02
Knoppix regognized my USB modem without problems, Havent tried it in ubuntu, because Now I have a new adsl-modem..

about 1 year ago I paid 38$ for a cheap external router/firewall/ADSL-modem,  which is connected to an ethernet-card.. (I can connect up to 4 computers to this modem)

Now it would probaply be a bit cheaper.

After buying this I havent had any problems. All operating systems I have tried regognize my ethernet card without problems, and that is enough to make the internet connection work... So no need to regognize the adsl-modem. as long as the ethernet card is regognized.. 

It is also really nice to have a hardware firewall.. before that I had some problems with windows, when the software firewall didn't start once, and I had to reistall windoze.. 1 reason, more to move to linux.

---

### Post by soul_rebel on 2006-08-02
please post the output of 
sudo lsusb
There are two different zyxel 630 models. They both can work with linux

---

### Post by Skyrail on 2006-08-02
> **soul_rebel said:**
> please post the output of 
sudo lsusb
There are two different zyxel 630 models. They both can work with linux

What did you mean abuot the first part about post the output of sudo lsusb? Where do I have to type that lol, I only got Ubuntu yesterday :) which I was really happy about. Also with the modem...do I have to install drivers or do I just plug it in and should it work? I'm just looking now to see where I can type that sudo lsusb, I've found out where to type it, in the terminal but It asks for my password and it won't let me type it :( hope I can get this sorted soon :)

---

