---
title: "internet problems"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Kyranor on 2007-06-08
Please can anyone help me.

I am trying to set up internet connection sharing in XP so that my second pc (ubuntu) can acces the internet.

I have a USB adsl modem connected to my XP PC and a ethernet network connecting the two pc's through a hub.

I can send files over the network no problem, also I can ping various websites on the ubuntu PC, which does not work when the USB modem on the XP PC is disconnected, so I know the connecting must be ok, is that right?

I have the network IP of my XP PC (192.168.0.1) in as the gateway and DNS on the ubuntu PC, is this correct?

Please help me... pulling my hair out here...

I am here right now so if anyone could talk me through mabye? Im completely new to linux. used to windows sorting everything out for me.

Thank you

---

### Post by Kyranor on 2007-06-08
sorry to reply to own post but does no one have any ideas? :(
I may be forced to resintall xp on the other PC if i cant sort this out...

---

### Post by viciouslime on 2007-06-08
Try setting DNS to: 208.67.222.222

Though what you have already should work... so maybe something else is wrong.

---

### Post by Rocket2DMn on 2007-06-08
You should be able to bridge the connections from the Network Connections folder in XP.  This is how I forwarded internet access to a secondary PC a few years back.
No work should have to be done on the Ubuntu PC in this case

---

### Post by viciouslime on 2007-06-08
> **Rocket2DMn said:**
> You should be able to bridge the connections from the Network Connections folder in XP.  This is how I forwarded internet access to a secondary PC a few years back.
No work should have to be done on the Ubuntu PC in this case

It sound like that side of things is taken care of:

"I can send files over the network no problem, also I can ping various websites on the ubuntu PC, which does not work when the USB modem on the XP PC is disconnected, so I know the connecting must be ok, is that right?"

That screams DNS issue to me...

---

