---
title: "netgear wg121"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by rootmaster23 on 2006-05-11
Hi!

This time a question in english!

I told you a few days ago that i have troubles installing ndiswrapper!
i got it but now i have a problem installing my wlan utility "netgear wg121"

I always get the msg "incorrect driver"!
now i deleted all drivers and installed the .inf driver from the ndis folder!
now i get the msg "driver present - hardware present!" 
i enter modprobe ndisdriver
and then i name the connection
and the further steps are not possible cause of any errors!
i was win user and used to auto-detect everything and it worked!
i have my ip-adress, subnetmask, gateway and physical adr.
hope you got some usefull hints for me?

greez!
Markus

---

### Post by macdo on 2006-05-11
You say that you're typing "modprobe ndisdriver" Is that a typo? 
Because if it isn't, try "modprobe ndiswrapper" 

Then type ```
ifconfig -a
``` and post output, please.

---

### Post by rootmaster23 on 2006-05-11
Hi my hero! :)

ndisdriver was only a typo!:) 
here the result of ifconfig -a

lo     Protokoll:Lokale Schleife
...      inet Adresse:127.0.0.1   Maske:255.0.0.0
         inet6 Adresse:  ::1/128 Gültigkeitsbereich:Maschine
         UP LOOPBACK RUNNING MTU:16436   Metric:1
         RX packets:214 errors:0 dropped:0 overruns:0 frame:0
         TX packets:214 errors:0 dropped:0 overruns:0 frame:0
         Kollisionen:0 Sendewarteschlangenlänge:0
         RX bytes:17311 (16,9 KiB) TX bytes:17311 (16,9 KiB)

sit0    Protokoll:IPv6-nach-IPv4
...      NOARP MTU:1480   Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 frame:0
         Kollisionen:0 Sendewarteschlangenlänge:0
         RX bytes:0 (0,0 b) TX bytes:0 (0,0 b)

Hope i've done right!
Thnx 4 ya help!
Markus

---

### Post by macdo on 2006-05-11
I'm presuming that you speak German. I don't, but I _think_ that this page: [http://www.linuxboard.de/forum/viewtopic.php?p=28601](http://www.linuxboard.de/forum/viewtopic.php?p=28601) is what you need...

And I'm nobody's hero: my motto is trial and error, and if I can get someone else to do the trials... :-)

I would however suggest that you start from scratch: 'apt-get remove ndiswrapper' and then reinstall with insructions above, if you have problems, at least...

---

### Post by rootmaster23 on 2006-05-11
In the german forum it seems that nobody knows the answer to my question! you have no idea?

Thnx 
Markus

---

### Post by macdo on 2006-05-11
Ah. 

Try typing iwconfig?

To be honest, I'm really guessing here - these commands helped me when I had problems with my linksys WPC54G...

---

### Post by rootmaster23 on 2006-05-11
Thnx 4 ya help!
i tried and i tried and a few minutes ago i checked all my syntax-errors and all my confusion-errors :) and now

IT WORKS!!!

Hope i'll get some more pleasant adventures with my ubuntu!!

greez!
Markus

---

