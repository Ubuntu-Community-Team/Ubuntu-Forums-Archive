---
title: "Need some help getting network up and running again."
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-03-31
I just can't seem to figure out what is the matter with my network. I go to the HP network info tab on the HP solution center and it shows the printer as ip=192.168.2.2. I do ifconfig on my laptop and it shows ip=192.168.2.2. What gives?? I know they can't both have the same ip address. Also when I try and print from the laptop (HP C5140 is ethernet connected to network) in the cups error log I see "cupsdAuthorize: Local authentication certificate not found!" Any ideas what happened? The printer worked just fine couple weeks ago, then nothing. I have three comps wired (ethernet) to a router. Toshiba Satellite pro - dual boot Dapper and xp, Compaq 5900Z - Dapper, Gateway Media Center Edition - xp. Only the XP comp can print. Please let me know if you need more info as this is driving me nuts !! Thanks in advance.

---

### Post by Jose Catre-Vandis on 2007-04-02
Whoah!

Is the printer a network printer? if so, then it is odd that it has the same Ip as your laptop.

If not, and the printer is connected to your laptop, then it will use the same IP to present itself to other PCs on the network.

How does the printer get its IP address if networked. Will it allow you to set a static IP, which you can reserve on the router?

Are you using DHCP to connect all your devices? if so, try setting your PCs to static IPs to see if this will resolve the problem, or reboot the router to refresh all the IPs under DHCP. Could be the router has got into a muddle.

---

