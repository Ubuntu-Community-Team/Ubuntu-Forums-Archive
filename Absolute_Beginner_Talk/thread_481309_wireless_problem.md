---
title: "wireless problem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2007-06-22
hey,

i would really appreciate someone guiding me a little for setting up my wireless. 

equipment:

linksys wrt54gl router
Intel 2200 wireless card


i would like to set up a WPA encrypted network.

---

### Post by atlfalcons866 on 2007-06-22
you need ndiswrapper

---

### Post by atlfalcons866 on 2007-06-22
go here [http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)

---

### Post by Inxsible on 2007-06-22
Do you want instructions on how to set up a WPA network or is your card giving you problems?

---

### Post by mendingo84 on 2007-06-22
i don't think my card is the problem
sorry for the late info but:  i'm on Kubuntu. knetworkmanager detects the network. i've already set up the router to use WPA Personal encryption. but when i try to connect(using knetworkmanager), i can only introduce a WEP pass (which, if i try to use the WEP encryption isn't accepted although it is the same i have listed in the router web interface) . i want WPA ( i read it is much safer)

---

### Post by mendingo84 on 2007-06-22
i'm sure the card works because if i use no encryption i can easily connect through wireless. also, i can easily connect using wlassistant and not knetworkmanager

---

### Post by mendingo84 on 2007-06-22
oh well...not sure what i did...but it works now! i reselected the wireless network and it asked for the WPA password that time. it TKIP password which i stored in kwollet. Does anybody know if this password has to be changed on a regular basis?

---

### Post by Ghosty.be on 2007-06-27
Strange thing is i had my intel 2200bg working here (used it for weeks) and at some point in time (probably after upgrades) i have a bit a similar situation as yours: i see networks, but i cannot join them even though the password stored in gnome should be ok. (I'll see how i can force to re-enter the password ...

---

