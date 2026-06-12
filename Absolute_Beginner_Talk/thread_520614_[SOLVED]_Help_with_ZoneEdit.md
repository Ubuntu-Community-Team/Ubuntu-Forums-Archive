---
title: "[SOLVED] Help with ZoneEdit"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by kennyn on 2007-08-08
Ok this is the deal, I have zoneedit working fine. I can get to my website by going to the following address:

[http://www.kennynproductions.com:81](http://www.kennynproductions.com:81)

I want to be able to hide the :81

Someone told me to use WebForwards: in ZoneEdit. But when I do this, it loses my dynamic IP address. Am I doing this right??

I set my web forward to be:

kennynproductions.com or [www.kennynproductions.com](www.kennynproductions.com) forward to
[http://www.kennynproductions.com:81](http://www.kennynproductions.com:81)

Like i said, i have to use zonedit because my ISP blocks port 80 and uses dynamic IP address'. 

Any help on not showing the port number would be great. Thanks.

---

### Post by m.malmros on 2007-08-08
Look at zoneclient.py.  This is a python script that updates zoneedit zones based on your dynamic IP.  Depending on your modem, use port forwarding or if you are really brave a DMZ.  The Zoneedit site is a bit tough to navigate, but there's a lot of info on this in the FAQ's.

---

