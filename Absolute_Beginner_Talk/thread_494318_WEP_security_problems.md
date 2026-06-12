---
title: "WEP security problems"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-06
Last hurdle on the internet marathon, and I don't have a clue what to do.
I've got my wireless card recognised
I've got my wireless card to detect my network
I can connect to the internet when i disable the security on my ap
But when I put the security back on, my internet goes :(
I've tried editing /etc/network/interfaces, i've tried iwconfig rausb0 essid<XXX> ap <XXX> key <XXX> and it still doesn't work
Also network settings crashes my computer whenever I try to change the settings of my wireless
Does anyone have any ideas whats goin on and what I can do?
Thankyou!

---

### Post by mikeyphi on 2007-07-07
All you should need to do is enter your hex wep code in System - Administration - network.
It is possible, if this is not working, that your router is set to only communicate with listed devices. Open your router admin page and confirm all the settings.

---

