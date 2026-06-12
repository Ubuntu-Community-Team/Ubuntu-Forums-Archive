---
title: "Wireless Connectivity ?!"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Accurax on 2007-04-18
Hi guys, I installed Ubuntu on my laptop a while back, but apart from some very basic "playing" I havn't had much chance to really get into it, up to my proverbial in php shaped alligators :D 

Ok, so im a little confused.

I can get an internet connection pretty easily with an ethernet cable, yet when i slot in my belkin wireless card and try to get a wireless connection I get nowhere fast.

In the networking menu, under connections i do the following:

1) select the wireless connection
2) click properties
3)Tick "enable this connection"
4)Enter the same ssid that my windows machines use for my network
5)select DHCP

ok..... then comes the bit that confuses me .... my wireless connection here is ussine a shared wep key... which i have been enetering in the relevant box .... but the only 2 options i have for "key type" are "ASCII" and Hexidecimal, Neither of which work.

When ive filled the form in i click ok and everything tells me its working.... connection is enabled apparently, but i cant actually get a connection... so im thinking i must be approaching the key from the wrong angle here..... 

Does anyone have any tips?

---

### Post by Accurax on 2007-04-18
hmm ok... i think its actually a driver issue....... 

now i think i need to learn how to actually install and run programs on my little linux box...... yes... i am at that basic a level here :confused:

---

### Post by meborc on 2007-04-18
have you converted your password to hex numbers before entering it to the field?

when you configured your wireless router, then it should give you also hex passwords that work as a wep key... my router for example changed my password "sikumiku" (an example) to 88BB6B7054 (example) so you might try to enter that...

ahh... i guess i'm not making any sence...

i use WPA as it is more secure... so i can not help you with the wep much

EDIT: ahh... you have not configured your wireless card? ... what is the make and model?

---

### Post by Accurax on 2007-04-18
unfortunatly its a crappy BT standard router.... so its wep and thats it, i too would prefer WPA, however the key looks like a hex value to me

eg:
2404 22044 509

(not my key... but thats its structure)

---

### Post by tommie74 on 2007-04-18
2404 22044 509 is your key? You have tried: 240422044509? (skipping the spaces)

---

### Post by sdswingr on 2007-04-18
I am having a similiar issue with a Belkin card. But with mine when I insert it into the pci slot it isn't even recognized, no power to the card or anything

ok so now the card powers up, I have both a belking, and a netgear, my computers knows they are there when plugged in.
I am attempting to access a wireless network at a coffee shop, so no password needed...still neither card is able to detect any networks

---

