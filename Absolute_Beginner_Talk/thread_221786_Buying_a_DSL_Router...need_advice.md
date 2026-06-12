---
title: "Buying a DSL Router...need advice"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by GaryReggae on 2006-07-24
Hi folks,

Can anyone reccomend a good but cheap DSL Router that will work with Ubuntu?  I can't really afford to pay any more than £20 but I have seen a few on EBuyer.com that might be OK:

[http://www.ebuyer.com/UK/product/90977](http://www.ebuyer.com/UK/product/90977)

[http://www.ebuyer.com/UK/product/48448](http://www.ebuyer.com/UK/product/48448)

None of these mention on the website whether they work with Linux but am I right in believing that most DSL routers will work anyway?

EDIT: I've found the official website for the first one on that list and under 'compatibility', it has a Linux 'penguin' icon.  I guess this is a good sign!

---

### Post by risbac on 2006-07-24
If you buy a routeur, usually you connect to it through an ethernet port, by opening the administration interface on a website, right? Ethernet is fully supported in Linux for years. By default, your routeur will have an IP address, you plug your cable, open Firefox/Opera/Whatever and enter this IP. There is no need for any driver to make it work, it's the beauty of Ethernet ;-)

So my 2 cents on this problem: I may be wrong, but to me all routeur works this way, just buy ANY routeur, it doesn't really matter.

---

### Post by tommcd on 2006-07-24
I assume you are in the UK.
I think pretty much any DSL modem should work. Just connect it by ethernet. If your ISP uses PPPoE just set eth0 (system>administration>networking) to DHCP and in terminal type: "sudo pppoeconf" (without quotes). Answer the questions and you're done.
At least that's how I do it. I have a Westell DSL modem and I'm in the USA. Hope this helps.

---

### Post by OU812 on 2006-07-24
I'd stay away from the 90977 (the first link) because the specs do not mention dhcp capabilities. Make sure your router has this capability (like the second choice).

john

Ooops, it does ... way at the end. Well, tough choice then. Maybe search for some product reviews?

---

### Post by bigken on 2006-07-24
Hi I have the wireless model of the 1st option safecom and the only problem I had was I had too change 1 of the settings in firefox ;)

---

### Post by GaryReggae on 2006-07-24
Thanks for your replies.  I think I'll go for the first one then.

---

