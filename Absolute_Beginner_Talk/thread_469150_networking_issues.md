---
title: "networking issues"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by coolperson on 2007-06-09
I installed Ubuntu 6.10 a while ago with the intention of installing linux MCE and i cannot get connected to the internet. Using this same computer and the same networking setup i had absolutely no problems connecting to the internet using Windows XP or fedora core 6.

 I have an onboard network card on my soyo dragon mother board and an airlink auto configuring switch(owned by me) attached to a linksys workgroup hub model# EFAH05W(owned by apartment complex) attached to a cable modem. I have multiple computers on both the switch and the hub and they are connecting to the internet fine. I have tried connecting it directly to both the switch and the hub with no success. Then a couple of weeks ago i went to my parents house for a week and brought my computer with me to work on it and with no change in setting or anything it connected to the internet fine(my parents have a linksys router). I just plugged in the Ethernet cord and it worked. So it seems there is a problem with Ubuntu communicating with my switch and hub. 

Also i tried adding a new network car even though my onboard one worked fine at my parents house and i could not figure out how to install it. The light blinks but it doesn't show up on ifconfig.

Any help or comments would be appreciated. If you have any questions just ask. Thanks!

---

### Post by sandwitch on 2007-06-10
Seems to me you know your way arround with computers. So i can asume you checked if ubuntu gets the card loaded and dhclient gets an ip for it? If you have an ip you can ping to another station? Does DNS work? Best way to fins your problem is to rule others out.

---

### Post by coolperson on 2007-06-10
I know my way around windows but i am new to Linux. I assume it gets the card loaded because it shows up as eth0 on ifconfig and it worked fine with my parents router.  I do not believe it is getting the ip address. No ip address shows up on ifconfig and it will not let me ping other computers on the same hub saying "network is unreachable". Is there an easy way to check for sure? 

Also i have tried setting a static ip address similar to other computers on the hub and it wouldn't connect and when i try to ping my another computer it actually tries and says "destination host unreachable" instead of instantly saying "network is unreachable".

I know what a domain name server is and what it basically does but i don't know how to check if it is working in Ubuntu. I would assume it is not if the network is unreachable. I think the problem is it getting an ip address. 

Thanks for the help if you have any suggestions or questions let me know. As of know im not sure what i could do other than buy a linksys router because it worked fine with it. But that seems wast full when other operating systems work fine with my hub. 

Thanks again.

---

### Post by pmg on 2007-06-11
Try booting without the network plugged in.  Once it's up and you've logged in, note the time and then plug in the rj45.  Give it a minute and go to "System -> Administration -> System Logs" and look at "daemon.log" and "syslog" for the right time.  If you want to get directly at the raw files they are in the directory /var/log.  If you post the relevent parts here someone may be able to help interpret them, or you could compare what you see in a working environment with the nonworking environment.

---

### Post by coolperson on 2007-06-13
Sorry it took so long to reply that crappy hub i had went out and the internet stopped working on all my computers. I now have my switch connected directly to my cable modem and it is connecting to the internet fine. I am just going to buy a linksys router. Thanks for the help guys!

---

