---
title: "Wireless Setup Help needed!"
date: 2005-06-25
forum: Absolute Beginner Talk
---

### Post by iLLUsiVE on 2005-06-25
Please forgive if this topic has been answered elsewhere or if this is the wrong area to post.


I have a Linksys wireless WPC54GS and would love to go wireless on the laptop. However I cannot at the moment. I have tried ndiswrapper under other distros of linux and at best had 'spotty' connections. Any help on setting up a wireless nic under ubuntu would be greatfully appriciated.

---

### Post by TheDude on 2005-06-25
[QUOTE=iLLUsiVE]Please forgive if this topic has been answered elsewhere or if this is the wrong area to post.


I have a Linksys wireless WPC54GS and would love to go wireless on the laptop. However I cannot at the moment. I have tried ndiswrapper under other distros of linux and at best had 'spotty' connections. Any help on setting up a wireless nic under ubuntu would be greatfully appriciated.[/QUOTE]


can you please enter this command?:

> lspci

I want to see what chipset you have. That matters more than who made it.  In the end you will probably have to fight ndiswrapper again, but maybe not.

---

### Post by iLLUsiVE on 2005-06-25
Among all the listed devices, I have:

Broadcom Corp BCM4306 802.11b/g Wireless LAN controller (rev 03).
I hope this is the info you wanted to see.

---

### Post by iLLUsiVE on 2005-06-26
[QUOTE=iLLUsiVE]Please forgive if this topic has been answered elsewhere or if this is the wrong area to post.


I have a Linksys wireless WPC54GS and would love to go wireless on the laptop. However I cannot at the moment. I have tried ndiswrapper under other distros of linux and at best had 'spotty' connections. Any help on setting up a wireless nic under ubuntu would be greatfully appriciated.[/QUOTE]
 I did some looking around on the distro cd and found a folder listed 'wireless tools'

/media/cdrom0/pool/main/w/wireless-tools  There are 4 files 2 are .deb and other 2 are .udeb files. Not knowing what to do, I left them alone. Maybe these can be used instead of ndiswraper or maybe their used in cunjunction with?

I keep getting a ping of sorts it would seem that the wireless is working but not working according to the network moniter icon in the top left? But I have heard that may be a possible bug/glitch?

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=iLLUsiVE] Maybe these can be used instead of ndiswraper or maybe their used in cunjunction with?
[/QUOTE]


ndiswrapper is the only way to get broadcom cards to work. Broadcom has a problem with Linux.

---

### Post by iLLUsiVE on 2005-06-27
[QUOTE=poofyhairguy]ndiswrapper is the only way to get broadcom cards to work. Broadcom has a problem with Linux.[/QUOTE]

Could you perhaps supply me with a few wireless nic cards manufacturers that can work with linux without the use of ndiswrapper. 

Belkin - MS (eek) - Siemens - Netgear ?

---

### Post by Mr. Electric Wizard on 2005-06-27
I can tell you that the MS adapters do not want to work either...

---

### Post by Mr. Electric Wizard on 2005-06-27
[QUOTE=TheDude]I want to see what chipset you have. That matters more than who made it.  In the end you will probably have to fight ndiswrapper again, but maybe not.[/QUOTE]

Love the avatar Lebowski... :grin:   Best movie of all time I think!

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=iLLUsiVE]Could you perhaps supply me with a few wireless nic cards manufacturers that can work with linux without the use of ndiswrapper. 

Belkin - MS (eek) - Siemens - Netgear ?[/QUOTE]


The manufacturer matters not...its the chipset that matters. Sometimes in another version of a card, the maker changes the chipsets. Its annoying. So you have to get the exact model number and make.

These work good:

[http://madwifiwiki.thewebhost.de/wiki/MadWifi](http://madwifiwiki.thewebhost.de/wiki/MadWifi)

And these work ok:

[http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php)

Here is the best list:

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

Anything with a "prism" or "atheros" chipset will work good.

I personally bought a Linksys WPC11 version 3 to avoid messing with the ndiswrapper. Its plug and play.

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=Mr. Electric Wizard]I can tell you that the MS adapters do not want to work either...[/QUOTE]

Actually I think this one works good out of the box (has the right chipset to):

[http://www.amazon.com/exec/obidos/tg/detail/-/B00006IJO7/ref=ase_absosystincho-20/002-7840819-2620042?v=glance&s=electronics](http://www.amazon.com/exec/obidos/tg/detail/-/B00006IJO7/ref=ase_absosystincho-20/002-7840819-2620042?v=glance&s=electronics)

---

### Post by iLLUsiVE on 2005-06-28
Any one have a walk thru for ndiswrapper on ubuntu? Prolly dosent make a difference but my brain is numb at the moment.

---

### Post by poofyhairguy on 2005-06-28
[http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=broadcom)

ok

---

### Post by iLLUsiVE on 2005-08-27
I wanted to take the time and say 'Thank you'! I appriciate all the help you all have provided to me and others!

As of right now, I am considering purchasing a new wireless NIC that is fully supported by linux/ubuntu, but before I do that I will battle it out with ndiswrapper. for now I am going hard wire.

Thank you, again!

---

### Post by Steve1961 on 2005-09-05
Don't give up on your broadcom card yet.  Just check out the ndiswrapper page at sourceforge and download the drivers you need.  Then install the source for ndiswrapper 1.2.  I haven't managed to get the older version that you can get from the repositories to work but 1.2 seems OK.

Instructions for installing can be found in this thread:

[http://ubuntuforums.org/showthread.php?p=334239#post334239](http://ubuntuforums.org/showthread.php?p=334239#post334239)

---

