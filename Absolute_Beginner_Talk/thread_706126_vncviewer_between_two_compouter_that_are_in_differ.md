---
title: "vncviewer between two compouter that are in different networks"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by protenniser on 2008-02-24
Hi all,

Here is my problem. I have a personal computer and a laptop. At home I can easily connect to my pc from my laptop by using vncviewer (that's cool!). All I have to do is to enter the ipadress like
vncviewer ip-address:0
However the main thing I want is to connect my pc from my laptop from my university which is naturally in another network. So is there anything (there should be) more I have to do in order to access my pc from the university?

All help is appreciated, thanks!

By the way, another problem I have is I am making the connection from gutsy to feisty. And in my laptop sometimes some boxes and text are not rendered correctly (there is only background image instead) any idea what is wrong?

---

### Post by .nedberg on 2008-02-24
You need to open some ports in your router. Probably port 5800 and 5900, both TPC and UDP. Check [portforward.com]("http://portforward.com") to see how to do that with your router.

---

### Post by protenniser on 2008-02-24
Hi,

I know how to port forward and thanks for your reply, however does the command I use stay the same after I portforward? I mean since I am connection through a different network, &#305; think that I sould add something to the command that represents it, am I wrong?

Regards...

---

### Post by .nedberg on 2008-02-24
You would have to use your external IP.

You can find it [here.]("http://nedberg.net/ip.php")

I would recomend using [no-ip]("http://www.no-ip.com/") and the no-ip client to get a hostname for your dynamic IP (if that is what you have).

---

### Post by protenniser on 2008-02-24
.nedberg, thank you very much.*Your seuggestion for external ip address really worked!
I'll also try your second suggestion about no-ip and let all know the results.

---

### Post by steveneddy on 2008-02-24
> **protenniser said:**
> .nedberg, thank you very much.*Your seuggestion for external ip address really worked!
I'll also try your second suggestion about no-ip and let all know the results.

no-ip is nice, but we prefer to use dyndns.com

just to give all of the choices, most of them, well, the most popular.

These two are probably the two most used.

---

### Post by protenniser on 2008-02-24
Thanks, I'll also give it a try then...

---

