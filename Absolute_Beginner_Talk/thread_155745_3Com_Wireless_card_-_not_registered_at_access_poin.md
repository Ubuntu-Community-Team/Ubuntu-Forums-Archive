---
title: "3Com Wireless card - not registered at access point"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by Anne-Marie on 2006-04-05
I installed Linux today, so I **do** qualify as an absolute beginner.

I am trying to set up my Dell Inspiron 4150 to connect to my wireless access point with a 3Com client card. It is named 3CRWE154G72 [Office Connect Wireless LAN Adapter] and should be usable out of the box, according to a document found somewhere on the wiki. 

The PCIbus recognizes the card, but no signal from the card sis recognized by my wireless access point. I have worked my way through this really helpful document: [https://wiki.ubuntu.com/WiFiTroubleshooting](https://wiki.ubuntu.com/WiFiTroubleshooting), and found that everything works as it should until I reach stage 8. 

In stage 8, I read > "Check whether the AP can "see" you! Log into your AP and check the logfiles. The MAC of your wireless card should appear there somewhere." 

It doesn't.

And then: > "If this is not the case then you most likely have mismatching wireless settings: Check '$ iwconfig' for "Rx invalid nwid" (wrong ESSID), "Rx invalid crypt" (mismatching authentification method/key), "Rx invalid frag" (I haven't got a clue)."This is exactly the output I get. 

OK: So the file /etc/network/interfaces says: 
> "iface eth1 inet dhcp
wireless-essid dotnett
wireless-key s:*****
auto eth1"
(where the starts represent my ASCII wep key). 
This seems right - the ESSID is right, and the wep-key is right. The Macadress of the wireless card is on the list of adresses permitted to access the network.  However, I cannot understand the first line here: What does "face eth1 inet dhcp" signify? What can I do now to trobleshoot further?

Would greatly appreciate help, and please remember that I am very inexperienced at using Linux and the terminal window.

---

### Post by Papa-san on 2006-04-05
ARGHHHHH!!!

I went thru this, and am trying to get links together in my signature to get peeps with these issues some specific help...!  I'm working on it!

Hang in there! It will be well worth the growing pains for you!

---

### Post by Anne-Marie on 2006-04-05
Hanging in.... Thanks! :-)

---

### Post by Papa-san on 2006-04-05
OK...back with the links.
I don't know if these will help or not. Try to see if any apply. The only other suggestion I can make is different WEP key entries. Mine is Hexedecimal, but the only way I made it work is by removing the 's:' before the key was entered... Don't know why it worked, 'cause it isn't supposed to, but it did work for me.
(I am VERY new as well, so if I am way off, I'm sorry!:rolleyes: )

---

### Post by Anne-Marie on 2006-04-06
Trudging on...

It seems that the problem is that i cannot start the card. It is switched off/disabled, and I can find no way to turn it on. 

The question now is: How can I enable the wireless card on my Dell Inspiron 4150? Any suggestions?

Thanks, papa-san for the links. It helps to have another beginner's favourite links, especially when the beginner is a few miles further down the road. :-)

---

### Post by mdmarmer on 2006-04-06
You may have version 2 of this card.  Version 1 works with prism54 driver, version 2 does not.

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

One person reported getting this version 2 to work with Linuxant driverloader

They have a free trial

[http://www.linuxant.com](http://www.linuxant.com)

Mike

---

### Post by Anne-Marie on 2006-04-06
Thanks! The linuxant-driver fixed it (almost) hasslefree. I'm now on the internet with my wireless client card. It's one small step, but it makes me really happy!:mrgreen: 
Thank you, I really needed all the help I could get.

---

### Post by Papa-san on 2006-04-06
Awesome!
Enjoy Ubuntu!

---

