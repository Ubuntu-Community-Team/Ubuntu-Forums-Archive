---
title: "[B][/B]Atheros wireless card"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by mikeee6562 on 2007-12-17
Hi, I just installed Ubuntu 7.10 and the wireless network card is not reconized. I have a Atheros ar5007eg card in the laptop i am useing. What should I do to solve this problem. 

thanks mike

---

### Post by mikeee6562 on 2007-12-17
dang it guys i need some help

---

### Post by lvleph on 2007-12-17
[Google is your friend.](http://techaspect.net/2007/11/04/how-to-wireless-ar5007eg-with-ndiswrapper-in-debian-and-ubuntu/)

---

### Post by mikeee6562 on 2007-12-17
I looked at the supported wireless card list and my Atheros AR5007EG card is not even seen by Ubunto 7.10. Am I out of luck or is there a solution? It is on my Toshiba laptop

---

### Post by CyberBob on 2007-12-17
There is a solution posted here:

[http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros]("http://ubuntuforums.org/showthread.php?t=512828&highlight=Atheros")


The above referenced post fixed my problem with the Atheros 5005? chipset in my Acer laptop although it specifically is written for the Atheros AR5007EG card.

Good Luck!

---

### Post by x-to-tha-t on 2007-12-18
What's your setup? Ubuntu 7.10 comes with the madwifi drivers already installed, so you should be able to pick up your card. It can be a pain getting wireless networking to just work on Atheros cards. I've just spent ages configuring slackware to work with it and it can't be that different. Also my entire home network is all configured wirelessly - what are you having trouble with?

X

---

### Post by stchman on 2007-12-18
> **mikeee6562 said:**
> I got to say tha getting my Atheros wireless network card to work is a little more than I can take.  I put Ubuntu 7.10 on my laptop and cannot get it to work. The solutions are so esoteric that I won't even try. I will keep Ubuntu on my desktop computer but not on my laptop, as without an internet connection it is a lot less useful. Maybe I will try later when it is supported in a fashion that I won't have to jump through so many hoops.

thanks mike

I have an Atheros wireless card on my laptop and Ubuntu supports it out of the box in Feisty and Gutsy.  What model Atheros wireless card do you have?  The restricted drivers are enabled by default.

I have a script that will install the madwifi on your system in case the restricted drivers don't work.

[http://www.stchman.com/tools/madwifi/madwifi_feisty.sh](http://www.stchman.com/tools/madwifi/madwifi_feisty.sh)

chmod the script to 755 and run as sudo.  Just make sure to disable the restricted Atheros driver first before running the script.

if all else fails you can get an Intel 3945 wireless card on ebay new for around $20.

---

### Post by gfd_2 on 2007-12-18
> **stchman said:**
> I have an Atheros wireless card on my laptop and Ubuntu supports it out of the box in Feisty and Gutsy.  What model Atheros wireless card do you have?  The restricted drivers are enabled by default.

I have a script that will install the madwifi on your system in case the restricted drivers don't work.

[http://www.stchman.com/tools/madwifi/madwifi_feisty.sh](http://www.stchman.com/tools/madwifi/madwifi_feisty.sh)

chmod the script to 755 and run as sudo.  Just make sure to disable the restricted Atheros driver first before running the script.

if all else fails you can get an Intel 3945 wireless card on ebay new for around $20.

Not to hijack this thread.... but will this script work for any cad or just an Atheros card?  I ask because I've been beating my head against the wall trying to get an intel based 64 bit system (HP dv6633us) to recognize my wireless card.  Everything else works....

Also... if I give up on the on-board wireless how well does 7.10 handle a USB dongle like the Linksys?

Thanks in advance!

---

### Post by tgalati4 on 2007-12-18
Well Mike, let me guess what kind of hardware you have.

Still trying . . . .

No wait . . . .

I give up.

How about posting (from a terminal):

>lspci -vv

>lsmod


It might be a simple as blacklisting an existing module that interferes with the correct one.

---

