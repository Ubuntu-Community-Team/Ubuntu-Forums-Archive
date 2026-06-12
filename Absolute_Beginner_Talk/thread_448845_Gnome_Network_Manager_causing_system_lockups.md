---
title: "Gnome Network Manager causing system lockups"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by cor2y on 2007-05-19
At first i thought i was imagining things but since i have installed Feisty on occasion the gnome network manager applet blinks every few minutes and then my whole system proceeds to lock up for a few seconds.
The funny thing is I am on a wired network so its not like it is losing a wireless signal.
Is there anyway to remove/replace this applet with what Edgy or Dapper was using.
I myself am not to familiar with what allowed the system to detect the wired connection in these previous releases.

---

### Post by n8bounds on 2007-05-19
yeah, you can remove nm-applet from your gnome sessions startup tab

there is a networking tool in system>administration I think (sorry kde user, forgetting gnome stuff)

you can always edit the /etc/network/interfaces file manually..

try this for now, open a terminal and say:

sudo killall nm-applet && sudo ifconfig eth0 dhcp && sudo dhclient

(assuming ifconfig thinks your wired network card is eth0)

---

### Post by cor2y on 2007-05-21
thanks a lot n8bounds that worked great.
While i have nothing against the gnome network manager for say laptops and wireless connections i do wish they'd kept the old way of connecting found in Dapper and Edgy.

---

### Post by n8bounds on 2007-05-22
maybe it should ask you what you'd like to do the first time a new user logs in (nm-applet or no?)

I turn it off on my desktops, and like it much better than using iwconfig on my laptops; its especially a pain if you have multiple nics in use simultaneously, but again, I use the old way there

one feature I would like to see added is a preferred dns setting (so I can use opendns no matter what WAP I connect to)

---

