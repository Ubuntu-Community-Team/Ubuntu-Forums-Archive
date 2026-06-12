---
title: "Problems connecting to wireless network"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by guitarzan on 2008-03-17
Hi all this is my first post. 

I tried out Ubuntu 7.10 Gutsy and I love it, apart from the fact that I cannot connect to the internet.
My wireless card appears to work, and the wireless networks show up, but I can not connect to any of them. I have Windows XP installed as well and it works fine with that wireless card. (I cannot get my modem to work in Ubuntu either, but I suppose that's another story.) So I can only connect to the Internet in XP.

I have done tons of forum surfing and have found loads of stuff, none of which seems to help. I've tried ndiswrapper and plenty of other stuff. 

I have a Compaq V5000 laptop, if that is any help. 

Argh, please help me!

---

### Post by spiderbatdad on 2008-03-17
are your wireless config settings enabled for roaming?

---

### Post by guitarzan on 2008-03-17
> **spiderbatdad said:**
> are your wireless config settings enabled for roaming?

yep.

---

### Post by theRightNee on 2008-03-17
could you state the make and model of your card? it could be possible that full support for the card is not availabe yet =[

---

### Post by guitarzan on 2008-03-18
It's a Broadcom BCM9431MCG

---

### Post by paul41wafc on 2008-03-18
[LIST]
[*]Open 'Add/Remove Applications'
[*]Click the 'Preferences' button
[*]Enter your password
[*]Tick all the boxes under "Downloadable from the Internet" on the first tab
[*]Press 'Close' then close 'Add/Remove Applications'
[/LIST]

Make sure you have an Internet connection via Ethernet for this bit.

[LIST]
[*]Go to System->Administration->Restricted Drivers Manager
[*]Check the box which says enable Broadcom Wireless etc
[/LIST]

This should do the trick, it did for my mate's laptop 2 hours ago. I think you have to do it this way because Ubuntu aren't allowed to distribute Broadcom's drivers or firmware but I'm not an expert on that sort of thing. Hope this works out for you :)

---

### Post by guitarzan on 2008-03-18
I tried it and it seems like it would work, only I can't get an Internet connection because the wireless one is my only one.

---

### Post by paul41wafc on 2008-03-18
You mentioned you were using a laptop, could you not simply sit by your wireless router and plug in an ethernet cable while the restricted driver is enabled?

---

