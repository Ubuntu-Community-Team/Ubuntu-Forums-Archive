---
title: "Various questions/problems"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by weavin42 on 2007-08-09
I installed kubuntu 7.04 (Feisty Fawn) on my Acer Aspire 5570-2977 laptop last week. I still have a few problems I'd like to have resolved if possible. The system has the intel T2080 dual core processor.

1) After some searching and tinkering, I got the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) to produce sound. To produce sound I needed to add the line:

options snd-hda-intel model=auto

to /etc/modprobe.d/alsa-base

However, I still have a few slight problems. #1 Whenever I plug in headphones, sound still plays through the laptop speakers and the headphones. I've tried adjusting the mixer in KMix but it controls both the headphones and the "front" laptop speakers. #2 The SPDIF output is not working, this output is shared with the headphones jack. I assume it is not working because it doesn't glow red like it did in vista. #3 I can use the Acer function keys to control the audio volume, (Fn + up/down key) but is there anyway to change the resolution? It jumps 9-10% each time, I'd like 4-5%.

2) I was able to get the wireless network card working (Atheros AR507EG) by following the guide here on the forums. [HOWTO]("http://ubuntuforums.org/showthread.php?t=512828"), it uses ndiswrapper (v1.47) and the windows xp drivers. I am connecting to a Belkin G wireless router (model #F5D7231-4). I'm having the following problems. #1) I'm not able to connect to widows shares on the network with samba (using Konqueror) but I can when I have eth0 connected to the router. I can see the windows shares when I'm just using wireless, it just doesn't connect. Also the router has been freezing up alot since I installed linux (might be fixed now that I've changed bittorrent clients). I'm also unable to connect to the router or ping it's ip, but I have no problems when I'm connected with eth0.

3) Anyway to mount my T-mobile Dash? I'd like to be able to sync it but I can use a windows machine if all else fails. I tried [synCE]("http://www.synce.org/index.php/SynCE-Wiki") but I'm running WM6 and haven't got that working yet.

Thanks for all the help,

Josh

---

### Post by phr0ze on 2007-08-09
I wish I could help you with some of this. For number 2 it sounds like perhaps your network IP settings are not correct. Are you using DHCP?

---

### Post by weavin42 on 2007-08-10
It's working over wifi now. I don't know why but after I restarted /etc/init.d/network it started working. That doesn't mean it's fixed but oh well. I'm still having trouble with bit torrent clients crashing or not seeding properly but that for another forum. I'd really like to get the audio working 100% or at least the headphone output to work properly. I'm sorta reluctant to mess with it myself because I'd hate for it to stop working but I've seen reports of people with the spdif output working with different distros. Otherwise I'm pretty happy with the switch to linux. I haven't used linux for 3-4 years so I'm pretty rusty.

Josh

---

