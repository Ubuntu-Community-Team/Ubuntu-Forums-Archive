---
title: "eth0:Media link during bootup"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by bzburr on 2006-07-03
hi
when booting ubuntu pauses for a very long time at

eth0:Media link on 100mbps full duplex (when booting in recovery mode)

what do i need to do to do to speed it up?
Buzz_the_beginner

---

### Post by HereInOz on 2006-07-03
After it boots up, does your ethernet interface work?  It sounds like the boot routine is trying to bring up the ethernet card, but it is failing.  Open a terminal and type in dmesg.  It will give you a full list of the boot up process.  Have a browse through it and see if you can find anything relating to eth0 and see what it says.  

That may give you some clues. 

Cheers,

Alan

---

### Post by bzburr on 2006-07-03
yeah the ethernet works fine
i'll try that command  and report back from here in Brisbane
cheers
buzz

---

### Post by HereInOz on 2006-07-03
It could still be a dodgey ethernet card.  Is it an on-board thingy or is it a PCI card.  Either way, I would put another one in there and see what happens, if you have one.

I have seen some wierd faults with on-board ethernet chips lately, to the point where I will believe anything.  Had one that would refuse to connect to about 3 particular web sites.  Change the card - bingo - works.  Who knows why.

---

### Post by u.b.u.n.t.u on 2006-07-03
If you have more than one ethernet in the list, try disabling those you aren't using.

System > Administration > Networking

---

