---
title: "Need help connecting to the internet"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by mihaaa on 2007-09-09
let me start like this, i know that this must be one dum question but still.. 

i have ubuntu on my pc for about a week, and the sad thing is that i first managed to get the internet, with the terminal (sudo pppoeconf) and it did wotk, but than i must have done sth wrong and i cant get the internet to work,.. have been looking thru the posts on different forums for days and nothing seems to work, but the main reason bein me not having a clue so PLS HELP, luckly i suspected that i could be capable of sth like this and i left windows on just in case,.. otherwise i wouldn't even be able to write this post since the internet at the time on my ubuntu is a no no :D .
maybe the wisest thing would be to reinstal sth or reset it ...
any help would be great,.. thnx

---

### Post by HereInOz on 2007-09-09
Give us information on your hardware:

What modem / router are you using?
Is it a USB or Ethernet connection to your computer?
DSL?  Cable?

---

### Post by mikewhatever on 2007-09-09
If you've done something wrong, you can just redo it by running the pppoe wizard again.

---

### Post by mihaaa on 2007-09-09
wow that was quick :) thanx guys

i use dell inspiron 9200 w. dell wireless 1350 wlan mini-pci rev 4.5 card, the connection is an adsl one, about the router,.. hm it is sinope 568+  (SI2000 Sinope568 IAD) it's a wireless router supplied by an internet provider.. as far as i know it is the ethernet connection

i thoguht about rerunning the pppoe wizard might help but it didn't,.. i repeated this few times :D

maybe this might help understanding the status

miha@Miha:~$ plog
Sep 10 00:29:03 Miha pppd[6339]: CHAP authentication succeeded
Sep 10 00:29:03 Miha pppd[6339]: CHAP authentication succeeded
Sep 10 00:29:03 Miha pppd[6339]: peer from calling number xy authorized
Sep 10 00:29:03 Miha pppd[6339]: not replacing existing default route through ppp1
Sep 10 00:29:03 Miha pppd[6339]: local  IP address xy
Sep 10 00:29:03 Miha pppd[6339]: remote IP address xy
Sep 10 00:29:03 Miha pppd[6339]: primary   DNS address xy
Sep 10 00:29:03 Miha pppd[6339]: secondary DNS address xy

br
miha

---

### Post by mihaaa on 2007-09-10
anybody... if i did't bost enough info please do tell me so and i will find additional..

---

### Post by mihaaa on 2007-09-11
ANYBODY?!?!
talking about supportive community, and I know about non replyed posts, I read it at the beggining and tryed to write one according to that notes, but stil there is only so much a man can write if he hasn't got a clue

---

### Post by mendingo84 on 2007-09-11
i had a similar problem ... every time i booted the connection failed to load. try this, it worked for me:
```
sudo poff
```
and after that:
```
sudo pon dsl-provider
```

if this doesn't work try to run the pppoeconf command again

---

### Post by mihaaa on 2007-09-11
thanx for a reply,.. 
I tried both before already, commands and starting the ppoeconf wiz again but didn't help..

---

### Post by zelezni on 2007-09-15
Hello Miha!

Do you have a special reason not to use pppoe connection established by sinope router? If not, navigate with your browser to [http://192.168.0.1](http://192.168.0.1), login with admin/admin (or it is user/user, click on internet and configure the connection. Then in ubuntu box enter default gateway to 192.168.0.1. That should work.

Pa lep pozdrav!
zelezni

---

### Post by mihaaa on 2007-09-17
hey zelezni, thanx for a reply,... i didn't quite get the part where you talk about "in ubuntu box enter default gateway to 192.168.0.1. ".. have tried to put it in a terminal as a command but wasn't recognised

lp
miha

---

### Post by zelezni on 2007-09-21
Miha!

Till now, you have used your PC to dial out to your internet provider. What I suggest is that you use your router to do that. In this case, your router will be constantly connected to ISP. Our job is then just to correctly configure your PC to be in the same network as your router and to use the default gateway, which is actually router's IP address.
From the box, sinope comes configured with address 192.168.1.1 (I've done a mistake in my previous post). First, you have to configure your PC to use the same IP class, e.g. 192.168.1.10. You can do that in menu *system>administration>network*, select *wired connection*,* properties* and change *IP address* to 192.168.1.10 and *Gateway address* to 192.168.1.1 and in *DNS* tab enter servers 193.189.160.13 and 193.189.160.23. After confirmation, you will be able to navigate with your browser to the address [http://192.168.1.1]("http://192.168.1.1") and login as admin (I forgot the exact login info, but you can check this in the manual of sinope568 ). Once being there, use the *Internet Access* link to enter your connection info. Choose PPPOE type, enter your username and password and that should be all.

Happy surfing!

---

