---
title: "VNCviewer works one direction but not the other. Need help please."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-26
I

---

### Post by skymera on 2007-07-26
Brilliant

---

### Post by jerrynewt on 2007-07-26
I've installed vncviewer on my Gateway desktop and my Toshiba Satellite Pro laptop. The Gateway can bring up the laptop just fine, but with the same settings (different address) the laptop can't bring up the Gateway. Any ideas as to why?? Thanks in advance.

---

### Post by skymera on 2007-07-26
are they wireless?
if they are they could be blocked behind the router,
that was my problem

---

### Post by jerrynewt on 2007-07-26
Sorry I hit the enter key by mistake in the first post. Guess I've been on here too long today.

---

### Post by skymera on 2007-07-26
indeed lol.
so are they wireless?

---

### Post by jerrynewt on 2007-07-26
No, my network is hardwired thru a linksys router. Both comps can ping each other just fine, and the traceroute is good for both.

---

### Post by skymera on 2007-07-26
i believe VNC uses TCP & UDP 5500 5800 5900

are these allowed through?

if im wayyyyyyy offcourse, im sorry

---

### Post by jerrynewt on 2007-07-26
Did a port scan on the laptop and the Gateway and both have 5900 open.

---

### Post by skymera on 2007-07-26
TCP and UDP.

5500
5800
5900

open them all, they all are sued  i believe.

---

### Post by jerrynewt on 2007-07-26
How do I do that. Not stupid just reallllllly slow !!

---

### Post by skymera on 2007-07-26
first you have to log into your router, i know my login.

then go to: [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

select your router and it should tell you how to forward ports.

hope i helped you

---

### Post by jerrynewt on 2007-07-26
Thanks for the help. This is the main reason I like linux so much -- someone is always there to help you, no matter how simple or complicated the problem. Windoz is becoming a dim memory. Thank you again!

---

### Post by skymera on 2007-07-26
no probs.

and they say 16 year old are useless. tut .

hope it all wokrs out right and have fun VNC'ing

---

### Post by jerrynewt on 2007-07-26
Footnote: Solved the problem by opening up network in admin and adding the ip of the Gateway to the hosts list. Fired up vncviewer on the laptop, typed in the Gateway host name and viola!! -- perfect!! Thanks again.

---

