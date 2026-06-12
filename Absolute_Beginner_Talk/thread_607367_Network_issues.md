---
title: "Network issues"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by hyby on 2007-11-08
Hi guys, 

I am currently having problems connecting online through my Ethernet connection. I can connect through windows via DHCP. I went into the network settings and changed the eth1 setting from roaming to DHCP. However, for some reason i still can not connect online. I also have wireless, but its turned off and left on roaming mode. 

Can i please get some advice.

---

### Post by Harpoon on 2007-11-08
I am not sure from your post, but I think you are trying to play with the wrong network card.  Wired networks generally show up as eth0, and wireless and eth1 (or perhaps something different like ath(*)).

My clue was when you set the card to roaming.  That's a wireless operation.

---

### Post by hyby on 2007-11-08
thanks for your reply. Can i just simply shut on or select over the other. In the past with 7.04 you can choose the adapter you plan to use. Is there a way i can do that?

---

### Post by Harpoon on 2007-11-09
Sorry for the delay on my side.  OK, if you are going to use wired networking, then probably the easiest thing to do is go to the network manager and choose "wired" (I don't remember if this will automatically de-select wireless, but I have a feeling it will).  Then, configure the setup -- don't remember if that is in a "properties" tab.  If not, right click it.  Then put in the info as it applies to your setup.  Close your way out and wait just a minute to see if the connection automatically appears.

If it does not do it automatically, then there are two steps to try.  Find the network manager icon and click on it, and it should say something like "disconnected" and ask if you want to connect.  If that is the case, say yes.

Otherwise, go to a terminal, and
sudo ifdown eth0 <should come back and say it is not configured>
sudo if up eth0 <should delay for a few seconds then return you to a prompt>
ifconfig <if you are running with DHCP, you should see an assigned internet address>
If you get this the icon should let you know all is well and you should be able to net around all you like.

I am working from faded memory on the network manager details, so forgive me if you wind up having to hunt around with the right-left click menus,

Good luck.

---

