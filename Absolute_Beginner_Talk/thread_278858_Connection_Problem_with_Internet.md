---
title: "Connection Problem with Internet"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by BIHAJDIN on 2006-10-17
I cant connect to the interent everythin else runs so perfect and its better then xp  but i just cant connect. It finds my interent and says actiontec which is what I connected to with xp  but i dont know how to connect with linux, can someone please help me ? 

Thanks a lot

---

### Post by yman on 2006-10-17
> **BIHAJDIN said:**
> I cant connect to the interent everythin else runs so perfect and its better then xp  but i just cant connect. It finds my interent and says actiontec which is what I connected to with xp  but i dont know how to connect with linux, can someone please help me ? 

Thanks a lot

does your internet provider provide support for linux? how do you connect to the internet? (dial-up, DSL, cable ect.). you need to provide information if you want answeres to your questions.

---

### Post by BIHAJDIN on 2006-10-17
sorry about that i connect with DSL wireless with Qwest

---

### Post by BIHAJDIN on 2006-10-17
bump

---

### Post by starsky on 2006-10-17
You need to do some hunting if iwconfig doesn't (specifically you need driver for your current wireless card).

**It doesn't matter, whether your ISP supports Gnu/Linux or not AFAIK**

Once you get iwconfig working, you need to get dhcp lease from your wireless modem. 
(sudo dhclient3 <whatever_your_wireless_device_maps to>). 
for me, e.g. (using intel 802.11b/g) -

$sudo modprobe ipw2200 
$iwconfig 
$iwconfig eth1 (this is my wireless device)
$sudo dhclient3 eth1
[....messages....]

$ ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
64 bytes from 10.1.1.1: icmp_seq=1 ttl=255 time=0.659 ms
64 bytes from 10.1.1.1: icmp_seq=2 ttl=255 time=0.655 ms
64 bytes from 10.1.1.1: icmp_seq=3 ttl=255 time=0.663 ms

--- 10.1.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.655/0.659/0.663/0.003 ms

I am now connected to my wireless modem.
You need to setup some specific values in your modem now 
(via www, SSH or telnet). This is given to you by your ISP. 

Hope it helps.

---

### Post by BIHAJDIN on 2006-10-17
no it dint help im sorry i don't get this I'll  just stick with windows but hey thanks a lot for your time and help everyone ](*,)

---

### Post by starsky on 2006-10-17
> **BIHAJDIN said:**
> no it dint help im sorry i don't get this I'll  just stick with windows but hey thanks a lot for your time and help everyone ](*,)

No probs. Anytime. :)

---

### Post by yman on 2006-10-17
maybe your missing a driver or whatever its called. I have that problem: I don't have drivers for my LAN card or my DSL modem so I can't connect to the internet with my ubuntu laptop.

---

### Post by BIHAJDIN on 2006-10-17
wow that umm really i don't know how to put it they should really fix it and make it easy to get on internet like windows

---

### Post by yman on 2006-10-18
> **BIHAJDIN said:**
> wow that umm really i don't know how to put it they should really fix it and make it easy to get on internet like windows

most people find it easy, but sometimes a comersial company chooses to ignor linux and then things go bad. they can't ignor windows because there are so many people who use it. it's not because windows is better but because it has over 90% marketshare.

there may be a solution to you problem, but I personaly don't know it. if you'll be patient and polite and don't blame linux for things that aren't it's fault you may get your problem solved. or maybe not. maybe you should try a different distribution. perhaps a comercial distribution would have support for your modem. I don't know.

---

