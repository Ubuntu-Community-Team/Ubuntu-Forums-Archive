---
title: "Noob attempting ubuntu wireless router"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by seaward on 2006-10-25
Hi,

I'm trying to make my ubuntu box serve the internet to my housemates' computers (they're both running windows xp) via an ad-hoc wireless network.  Seems simple enough except i'm a bit retarded about networking in linux.

What i've essentially done so far is set up eth0 (which is hooked up to the internet) and wlan0 (which is for my housemates to hook on to) and then tried to create a dhcp server so that ips are given to each computer dynamically.

According to my syslog, all of the dhcp requests that my ubuntu box is receiving are being responded to correctly with offers of an ip address.  But the kicker here is that the windows computers are completely ignoring the ip addresses handed to them and eventually just fall back on a self-assigned private ip address.  Obviously this is totally useless because the computers cant talk to each other.

Sorry for the longish post but this is doing my nut in and I can't fathom a reason that this is happening.  Whats doubly annoying is that when i use windows to act as a dhcp server, there is no trouble whatsoever, so i am 99% sure that this problem is with my comp and not with my housemates'.  Grr.

I hate to use a well worn noob phrase but, "windows can do it so why can't ubuntu?"

Cheers for any help you can offer!

---

### Post by x64Jimbo on 2006-10-25
There's a tutorial for this here:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by seaward on 2006-10-25
Thanks for the reply but I've already attempted this HOWTO and several others as well.  I wouldnt be asking if I hadn't already searched extensively for a solution.

Cheers tho!

---

### Post by x64Jimbo on 2006-10-25
fair enough. thank you for searching. you are one of very few.

---

