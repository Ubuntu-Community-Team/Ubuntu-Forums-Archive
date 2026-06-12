---
title: "chillispot woes"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by grandtheftautumn on 2007-05-08
Hey everyone,
I'm a windows guy venturing into the wide world of Linux, and my first major project, which seemed easy at first but has proven to be much more of a hassle than anything, is setting up a chillispot server. I have been referring to [https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot](https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot), but it is way too advanced for me at this point. My problems lie in the fact that i don't know how to "run the command 'modconf'". 

> Chillispot create a VPN, that is to say an IP tunnel. Your kernel must support this: if you're using software such as OpenVPN chances are you're already fine. Anyhow, take a look at the following section in your kernel configuration (run the command 'modconf'): Linux Kernel Configuration: TUN/TAP support

Kernel/drivers/net --->

    *

      tun [Universal TUN/TAP device driver support] --->

You can either compile the TUN/TAP support inside the kernel or (as is this example) build it as a module. The name of the module will be tun.

You'll probably also need to enable IP masquerading, NAT or what is necessary in order to let the VPN clients surf the outside network. If you're reading this HOWTO it's likely that you already know all of this; if not, look around for specific documentation. 

I also have no idea how to do anything in the last paragraph....any suggestions? I will definitely be back with more questions.

Thanks in advance.

---

### Post by grandtheftautumn on 2007-05-08
Maybe it would help too if i let you know what i was trying to do exactly, maybe there is a better solution out there than Chillispot. 

Allowing several accounts online at once, with numerous users under each account
Separate bandwidth throttling for each account
A customizable login page
Ability to block users by MAC address

Other things of importance:
Porn filtering (i know chillispot probably doesn't do this)
Blocking of P2P protocols (was going to use DDWRT for this but if there is something better, i'm interested)

These accounts will be free so there is no need for a billing system

any thoughts?

---

### Post by orb9220 on 2007-05-08
[http://www.easylivecd.com/english/hotspot.html](http://www.easylivecd.com/english/hotspot.html)
[http://www-128.ibm.com/developerworks/linux/library/wi-wiisp.html](http://www-128.ibm.com/developerworks/linux/library/wi-wiisp.html)
[http://www.publicip.net/](http://www.publicip.net/)
[http://www.wi-fiplanet.com/tutorials/article.php/3357611](http://www.wi-fiplanet.com/tutorials/article.php/3357611)

all with just a google search on:  Linux hotspots

---

### Post by eltorodeoro on 2007-05-08
that's all above my head, as well, but a great book i've been reading the last few days is the O'Reilly "ubuntu hacks".  you should double check, obviously, but i think there may have been some portions relevant to your situation.

---

### Post by grandtheftautumn on 2007-05-08
zonecd sounds perfect...no complicated setup, free, filtering, user control......perfect.
don't know why i never stumbled across it before.

thanks for the replies, i'll let you know how it works out.

---

### Post by ispyisail on 2008-03-27
> **grandtheftautumn said:**
> Hey everyone,
I'm a windows guy venturing into the wide world of Linux, and my first major project, which seemed easy at first but has proven to be much more of a hassle than anything, is setting up a chillispot server. I have been referring to [https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot](https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot), but it is way too advanced for me at this point. My problems lie in the fact that i don't know how to "run the command 'modconf'". 



I also have no idea how to do anything in the last paragraph....any suggestions? I will definitely be back with more questions.

Thanks in advance.


***First question**
If you got back to the wiki site you will find it is now updated to fix your problem 

***Second question**
The information in the wiki rubbish, chillispot has a built in DHCP server so you don't need IP masquerading

The ubuntu chillispot wiki currently  has many errors and unless you know what you are doing it would be very hard to complete the project (subject to change)

If you want a complete howto you could try

[https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot6.06]("https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot6.06")

Unfortunately its only for ubuntu 6.06 but its complete

---

