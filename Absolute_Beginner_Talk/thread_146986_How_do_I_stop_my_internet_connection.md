---
title: "How do I stop my internet connection?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Kersus on 2006-03-19
Heya, so I finally got connected to the inet.  pppconfig and pon didn't work but editing the wvdial.conf and wvdial worked fine once I was set up.

So now I have a problem.  I have NO IDEA how to end my internet connection.  Help!

Also is there any way for me to see what my connection speed is and stuff like that?

Kersus

---

### Post by beej101 on 2006-03-19
this is how i would disconnect mine...
click on the network monitor
click on configure button
disable the interface that you use to connect to internet...
as far as knowing speed, i'd also like to know

---

### Post by xenmax on 2006-03-19
"/etc/init.d/networking stop"  - but i think this will completely disable all networking - not just the internet. If you want to just stop internet, but access some other n/w you are connected to, i can;t help you there.

---

### Post by Kersus on 2006-03-19
Yeah, I'm networked with another PC (running XP), so I just want to stop the internet connection part.

---

### Post by cwaldbieser on 2006-03-19
[QUOTE=Kersus]Yeah, I'm networked with another PC (running XP), so I just want to stop the internet connection part.[/QUOTE]
```

$ sudo poff

```
ought to still work, because you pretty much have to be using pppd at some level if you have a PPP connection (dial-up).

You might also be able to stop the pppd service if that doesn't work.

---

### Post by catlett on 2006-03-19
I don't know if this is what you mean, but InternetFrog.com has connection speed tests. It has one that is a standard download/upload test and one that is a VOIP test that deals more with broadband, packet size and delay. You need to have Java to run them. If that was it hope it helps.  If you meant something else excuse my ignorance and disregard.

---

