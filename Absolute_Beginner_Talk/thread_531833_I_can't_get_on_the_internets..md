---
title: "I can't get on the internets."
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by ICbacon on 2007-08-22
I received a Dell inspiron 2650 second hand from my aunt today and promptly loaded Dapper 6.06 (it's all I had).  I have been searching the forums to find solutions to my wireless issues and had a few questions.

I should start by saying I have two wireless hardware choices at my disposal, a netgear WG111T USB dongle and a belkin F5D7010 notebook card. Neither of which seem to be great, but if I can to this without buying new hardware I would be very happy.

1.) Is using ndiswrapper to use the windows driver that came on the netgear CD a reliable option?

2.) How do I figure out which chipset is used on the Belkin card?  There are drivers available for certain chipsets.

3.)  I haven't looked for this yet, but if anybody has a link to a good terminal guide I would be very grateful.  This is literally my first day with Linux and feel very dumb right now.

Thanks in advance.

---

### Post by HW_Hack on 2007-08-22
Oh boy --- Linux on laptops can be a challange - I've ran both Ubuntu 6.06 and 7.04 on my Dell laptop which has Broadcom (chipset from hell) wireless. Both times using a NDIS driver worked but I'll be honest - I was only able to do by following some semi-complicated instructions posted here on the forums ... and those would only work for a particular version of Broadcom chips.

Be persistent and patient and you will certainly learn a few things.

try this 
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

you should be able to google the belkin adapter and see what its chipset is --- you will need the chipset and rev info - get the XP driver - and find an NDIS example for your particular wireless chip.

---

### Post by ICbacon on 2007-08-22
I'm going to focus on the Belkin card for now.  It looks like the most promising solution.  Where were the semi-complicated directions located at?  I don't know Linux, but I pick up stuff pretty quick.  This whole OS  switch started out as  something I could tinker with anyway, so complicated stuff is at least a starting place.  Thanks for the quick reply.

---

### Post by ICbacon on 2007-08-22
Okay, so when I go to system>administration>networking, under wireless connection, it shows that "the interface ath0 is active".  Does this mean the card is recognized but lacking a driver?  How do I figure out which chipset is on this card.  Can I use the serial number or something?

---

### Post by WebSiteGuru on 2007-08-22
does your wireless network have WEP or WPA? If yes you will have to configure it and put the Password.

---

### Post by ICbacon on 2007-08-22
The network we use at school is open.  We have to sign in, but there is no key needed.  If it's being identified, is it working?  I couldn't get any signal on campus. Everyone around me did.  Am I making this harder than it is?  I will try again tomorrow.

---

### Post by Majorix on 2007-08-22
Did you try clicking on the "two monitors icon" at the top right? There it should show you some network names and you can click one of them to connect. If this works, then your wireless card is working and you don't have to do anything.

---

