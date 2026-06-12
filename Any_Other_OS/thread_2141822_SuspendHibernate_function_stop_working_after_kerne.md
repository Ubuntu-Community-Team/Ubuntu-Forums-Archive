---
title: "Suspend/Hibernate function stop working after kernel v. 3.2.0-4"
date: 2013-05-03
forum: Any Other OS
---

### Post by kabukiM0n0 on 2013-05-03
Hi guys. 

I come here to see if anyone knows anything on the subject. 

I use #! 11 - which was working fantastic up until a few weeks ago when I dist-upgrade and it seems that the kernel was upgraded and since then suspend and hibernate don't work properly. 
They shutdown just fine, but when the system is brought back up - instead of the login screen one would expect to see, I get a flashy colored screen - where everything is working fine, as if I'm playing music it starts again, but I can't see anything - the only option is to ctrl+alt+F1, which is a black, green or red screen (they change color for some reason) and I then have to manually reboot. 

It seemed that the problem was the kernel and it's integration with m$ hardware. I'm running an Acer Aspire One d270 with gma500.
Anyway, I upgraded to v3.9 which is meant to have better intel integration but it still does exactly the same thing. 
I was looking around a bit in the Arch and Gentoo forums/wiki and found similar problems which unfortunately didn't work - so I'm thinking it might not actually be the kernel but something of some script that's gone haywire somewhere and was lost in translation. 

Also if I reinstall to v.3.2.0 it works no problem, the problems start  once the upgrade is finished. Also - putting the kernel on hold and  upgrading does the trick - but my gma500 doesn't kick in and I'm left  with generic vesa driver which makes everything look horrendous. 


Does anyone have any ideas what could be causing this? any thoughts or input it appreciated.

---

