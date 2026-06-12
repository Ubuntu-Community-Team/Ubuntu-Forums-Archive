---
title: "Cannot Connect to Internet"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by ashzoomerintrack on 2007-11-16
Hi guys i have just installed Ubuntu 6.06 2 days ago. Everything is just fine. But there is a problem i have the D - Link DFE-520 Tx Ehternet adapter. I have the drivers for it on CD for Linux 2.4 & 2.6 but unable to install them. Also guide me to install a dial up shortcut for BroadBand PPPoE WAN Miniport internet connection. Plz help me...:lolflag:

---

### Post by overdrank on 2007-11-16
> **ashzoomerintrack said:**
> Hi guys i have just installed Ubuntu 6.06 2 days ago. Everything is just fine. But there is a problem i have the D - Link DFE-520 Tx Ehternet adapter. I have the drivers for it on CD for Linux 2.4 & 2.6 but unable to install them. Also guide me to install a dial up shortcut for BroadBand PPPoE WAN Miniport internet connection. Plz help me...:lolflag:

HI and welcome, from what I can find on the D link card is that it should work fine on ubuntu. Have you looked in system, administration, network and see if the card is recognized?

---

### Post by hihihi on 2007-11-16
how about installing ubuntu 7.10?
its another story, much better ubuntu, no compare.
BUT who knows why you are running 6.06 NEVERTHELESS HERE A LINK THAT MIGHT HELP U:
[http://ubuntuforums.org/showthread.php?t=536079&highlight=dwl-g122](http://ubuntuforums.org/showthread.php?t=536079&highlight=dwl-g122)

---

### Post by ashzoomerintrack on 2007-11-16
Thanks for yor modest help guys!!! 
Now Getting connected to internet by doing **pon dsl-provide**r but the connection gets lost saying modem hung up. Also i am able to access only pages like Google , Gmail, Yahoo, Yahoo MAil, getdeb but many of the pages firefox says connecting but the pages are not downloaded. Please help me. Also there seems to be some problem

[http://img111.imageshack.us/my.php?image=prob1kp9.png]("http://img111.imageshack.us/my.php?image=prob1kp9.png")

---

### Post by Andy Norfolk on 2007-11-17
I don't reckon 7.10 would necessarily solve the problem. Feisty worked very well with my Safecom external ethernet modem. Gutsy just won't. I've blacklisted ipv6 which gets Firefox working, but I can't get at updates, software repositories etc. It's drivng me potty.

---

### Post by ashzoomerintrack on 2007-11-30
The problem was solved succesfully due to the support  but something has gone wrong from yesterday. It is not possible to connect to the internet for a long time..The terminal shows this:
Instance No. 1

reliance@reliance-desktop:~$ plog
Dec  1 08:49:43 localhost pppd[5083]: Using interface ppp1
Dec  1 08:49:43 localhost pppd[5083]: Connect: ppp1 <--> eth0
Dec  1 08:49:46 localhost pppd[5083]: CHAP authentication succeeded: Authenticat ion success,Welcome!
Dec  1 08:49:46 localhost pppd[5083]: CHAP authentication succeeded
Dec  1 08:49:46 localhost pppd[5083]: peer from calling number 00:E0:FC:40:B0:CD  authorized
Dec  1 08:49:46 localhost pppd[5083]: Cannot determine ethernet address for prox y ARP
Dec  1 08:49:46 localhost pppd[5083]: local  IP address XX.XX.XX.X
Dec  1 08:49:46 localhost pppd[5083]: remote IP address XX.XX.X.X
Dec  1 08:49:46 localhost pppd[5083]: primary   DNS address XXX.XXX.XXX.XXX
Dec  1 08:49:46 localhost pppd[5083]: secondary DNS address XXX.XXX.XXX.XXX



Instance No. 2

reliance@reliance-desktop:~$ plog
Dec  1 08:52:44 localhost pppd[5273]: local  IP address XX.XX.XX.XXX
Dec  1 08:52:44 localhost pppd[5273]: remote IP address XX.XX.XX.XXX
Dec  1 08:52:44 localhost pppd[5273]: primary   DNS address XXX.XXX.XXX.XXX
Dec  1 08:52:44 localhost pppd[5273]: secondary DNS address XXX.XXX.XXX.XXX
Dec  1 08:54:46 localhost pppd[5083]: No response to 4 echo-requests
Dec  1 08:54:46 localhost pppd[5083]: Serial link appears to be disconnected.
Dec  1 08:54:46 localhost pppd[5083]: Connect time 5.0 minutes.
Dec  1 08:54:46 localhost pppd[5083]: Sent 169757 bytes, received 1802400 bytes.Dec  1 08:54:52 localhost pppd[5083]: Connection terminated.
Dec  1 08:54:52 localhost pppd[5083]: Modem hangup
reliance@reliance-desktop:~$ poff dsl-provider
/usr/bin/poff: /bin/kill failed.  None stopped.
reliance@reliance-desktop:~$ poff dsl-provider
/usr/bin/poff: /bin/kill failed.  None stopped.



Help me..........

---

### Post by ashzoomerintrack on 2007-12-01
Help me.............

---

