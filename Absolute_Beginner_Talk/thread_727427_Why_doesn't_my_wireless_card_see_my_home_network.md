---
title: "Why doesn't my wireless card see my home network?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-03-17
I was using Hardy Alpha, but it puked on me recently (hey, I was warned!), and I had to reinstall. I'm now in Feisty, and suddenly my wireless card is blind to my home network. It's an integrated Intel card on an HP laptop, and it's worked with every other Linux distro I've ever used. It's located at eth1, and my wired connection is at eth0. The wired connection is working fine (that's how I'm accessing this site right now); the wireless card is recognized, but it won't find any networks. The options I get are "Connect to Other Wireless Network," "Create New Wireless Network," and "Manual Configuration." I know those wouldn't be there if Ubuntu didn't know my wireless card was present. Also, two other machines in the house are functioning fine on the network, so I know it isn't an issue with the router.

Any help is appreciated. Thank you!

---

### Post by spiderbatdad on 2008-03-17
Hardy changes may be stored in cmos. Power down remove battery...let sit for 10 minutes, possibly even remove RAM and reinsert.

---

### Post by Tatty on 2008-03-17
Try installing Gutsy...

There were a lot of problems in feisty related to wireless cards...  I had problems with it on my laptop  on feisty, but it worked out of the box in gutsy.

If you dont want to install gutsy, try booting from a live cd and see if it works...

---

### Post by doctorbighands on 2008-03-17
It doesn't want to work in the live CD versions of Feisty or Gutsy or OpenSuSE 10.3 or CentOS or Knoppix.

I didn't see any point in loading others. :)

I'm not convinced that this is anything Hardy did, but I suppose it could be. My wireless worked in Hardy up until the very last moment.

I don't want to install Gutsy on this machine - that's why I'm in Feisty right now. Gutsy does really funny (and not-so-funny) things to my HP laptop, as I've heard it does to many others. Besides that, I've never had a previous issue with this wireless card in Feisty before.

Still puzzled...

EDIT: I just tried removing/reinserting the battery, and it doesn't seem to have helped. The issue remains as it was.

---

### Post by spiderbatdad on 2008-03-17
I had the same problem, Doc. I assumed something was stored in RAM so I cleared it and all was well.

---

### Post by Miljet on 2008-03-17
I had a similiar problem in Gutsy. This is what worked for me. Hope it helps.

[http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf](http://ubuntuforums.org/showthread.php?t=603154&highlight=gilf)

---

