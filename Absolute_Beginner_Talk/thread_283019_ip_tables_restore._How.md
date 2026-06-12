---
title: "ip tables restore. How?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by geokok on 2006-10-23
In an effort to get ekiga to work I used a script the developers
provided in the apps documentation. It had to do something with configuring
ip tables. The result? A system that can not connect to the internet....

How can i restore the default ip table rules?

and if the first is solved, how can i get ekiga to work cause neither the 
script nor port forwarding worked for me.

PS I am on edgy eft but I posted here cause i dont think it has to do
anything with the version of ubuntu. Just me breaking my system....again..

---

### Post by geokok on 2006-10-23
It seems that after a restart the internet connection is back on....now what about that ekiga thing....?

---

### Post by Marsolin on 2006-10-23
I assume that you are using a router to connect to the internet. What about port forwarding didn't work?

You might also want to use a firewall utility like [Guarddog]("http://linuxappfinder.com/package/guarddog") or [Firestarter]("http://linuxappfinder.com/package/firestarter"). Using one of those you can turn your firewall on or off to test if that is part of the problem or if it is something else.

---

### Post by geokok on 2006-10-23
I have a Thomson speedtouch 530v6. 
I tried to forward the ports for sip (5000-5100) but didnt seem to make a difference,,....and I could configure &#956;torrent ports (for windows) properly so i guess the router is fine....

---

