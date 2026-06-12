---
title: "Crazy Slow Internet"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-01-13
I did a fresh install of Gutsy on my roommate's desktop the other day but I've noticed that the internet on his machine is painfully slow.  His pc isn't the fasted around or anything but it's a fresh install of ubuntu it should cruise at a reasonable speed.  I'm using the same network right now on my laptop and I can zip through web pages.  What would cause his internet to be so slow?  He's using a wireless connection with about 90% signal strength

Also, half the time I get a "Server Not Found" error from firefox when it just times out and gives up trying to load a page

---

### Post by sports fan Matt on 2008-01-13
Is there a possibility of alot of people trying to access the sasme siginal wirelessly? Have you tried to find a different wireless siginal? I am guessing logically cause I have no honest idea   (im guessing from windows so pardon my ignorance, but it sounds like maybe there are alot on the wireless network at one time?

Im taking a shot in the dark like I said, it may not be any of that, just trying to help..:)

---

### Post by HermanAB on 2008-01-13
Most likely he has a lame DNS listed in /etc/resolv.conf.  Compare the files on the two machines.

Cheers,

Herman

---

### Post by cartisdm on 2008-01-13
> **sox fan Matt said:**
> Is there a possibility of alot of people trying to access the sasme siginal wirelessly? Have you tried to find a different wireless siginal? I am guessing logically cause I have no honest idea   (im guessing from windows so pardon my ignorance, but it sounds like maybe there are alot on the wireless network at one time?

Im taking a shot in the dark like I said, it may not be any of that, just trying to help..:)

That's possible but weird.  I've just noticed that whenever I turn on his computer our network gets really slow for everyone.  It's not always as bad but it is definitely noticeable.  For the record we have 7 computers accessing wirelessly....

---

### Post by sports fan Matt on 2008-01-13
yeah..7 computers isnt much...Id attempt Herman's suggestion as well..I know on my brother's lappy you may have id say like over 15 (big area he lives in) I personally dont know much about networks, i repaired and did software tech things..:)

---

### Post by ryanVickers on 2008-01-13
I second that - if there's never been over 7 people, or 17 for that matter, than that's not the problem (unless they're all downloading full capacity ;))

I would check for some local issue with the drivers and related files...

---

