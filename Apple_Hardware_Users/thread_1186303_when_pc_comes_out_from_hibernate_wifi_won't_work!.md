---
title: "when pc comes out from hibernate wifi won't work!"
date: 2009-06-13
forum: Apple Hardware Users
---

### Post by gagginaspinnata on 2009-06-13
I've a macbook pro intel core duo 1,83 ghz with ubuntu 9.04.
Everything is working great. Wifi is even well working.
When I hibernate the mac, when it cames out from hibernate the wifi won't work! It doesnt find any hotspot!
Any ideas? :D

---

### Post by dwight on 2009-06-13
I have a somewhat similar problem with my macbook. Although I can still find and connect to wifi networks, I cannot access any websites or ping any servers. Only thing that helps is a reboot.

---

### Post by gagginaspinnata on 2009-06-14
> **dwight said:**
> I have a somewhat similar problem with my macbook. Although I can still find and connect to wifi networks, I cannot access any websites or ping any servers. Only thing that helps is a reboot.

Well I'm not alone!l
There must be something to do...

---

### Post by hachaboob on 2009-06-14
Turn off wireless and turn it on again.

---

### Post by gagginaspinnata on 2009-06-15
> **hachaboob said:**
> Turn off wireless and turn it on again.

I've just tried it but doesn't work :(

---

### Post by tiagobt on 2009-06-15
What if you unload and load the wireless driver?

Try the following commands:
```
sudo modprobe -r wl
sudo modprobe wl
```

---

### Post by gagginaspinnata on 2009-06-15
> **tiagobt said:**
> What if you unload and load the wireless driver?

Try the following commands:
```
sudo modprobe -r wl
sudo modprobe wl
```

Nope, doesn't work :(
Any ideas? Noone has this problem?

---

### Post by cyberdork33 on 2009-06-15
I actually think this is a normal issue... basically the fix is likely to be to unload the network modules before suspend and reload them on resume. Can you please identify your wifi hardware and your Mac hardware version (as instructed [here]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"))?

---

### Post by gagginaspinnata on 2009-06-15
> **cyberdork33 said:**
> basically the fix is likely to be to unload the network modules before suspend and reload them on resume. 

YES!!!! WOW it works great :D:D:D:D:D:D:D Realy thanks man, you've saved me!!!!



[HTML]Can you please identify your wifi hardware and your Mac hardware version (as instructed [here]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"))?[/HTML]
Anyway, the wireless chipset is 
[HTML]$ lspci|grep Atheros
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)[/HTML]

---

### Post by cyberdork33 on 2009-06-16
ok well since you have an atheros-based card, the directions in some of the above posts will, of course, not work for you since they are referring to modules for the Broadcom-based wifi cards.

Your driver will be the ath5k or ath9k module.

Glad you got it working, and please remember to identify your mac version properly (as in the previously posted link) when asking for support so that we know what hardware we are dealing with.

---

### Post by gagginaspinnata on 2009-06-16
> **cyberdork33 said:**
> ok well since you have an atheros-based card, the directions in some of the above posts will, of course, not work for you since they are referring to modules for the Broadcom-based wifi cards.

Your driver will be the ath5k or ath9k module.

Glad you got it working, and please remember to identify your mac version properly (as in the previously posted link) when asking for support so that we know what hardware we are dealing with.


Of course, next time I'll properly identify my mac versione before posting! Thank you so much!

---

