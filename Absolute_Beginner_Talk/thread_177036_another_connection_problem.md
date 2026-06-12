---
title: "another connection problem"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-05-15
hi !
I've been searching the forum for an answer but I did not find one so here's my question.

I did not installed linux yet but I've been spending some time with the live ubuntu cd.
It did reconized my network card but in order to connect to the internet I must (even in winxp) type my username and password.

I did not find this option in the connections on ubuntu.

what shell I do ???
how / were do I type my username and password given my by my internet provider ???

p.s
I'm using automatic IP address and DNS
Ethernet
adsl

thanx ahead !!!

---

### Post by MaximB on 2006-05-15
I hate doing this but my question skipped a page so does my chances for reply...
plz help....

---

### Post by ProjectGod on 2006-05-15
pppoe broadband / adsl is "always on" meaning. you shouldnt have to connect to it via the usual username / password dialog so common with dial up. 

strange that you should have to insert these credentials in windows xp to get adsl connection.

if the adsl router is "automatic ip address" enabled etc etc. 

all you need to do on ubu is enable DHCP on the ethernet interface, and set the ISP's DNS server's IP address... ring em up or check your diary!

after this open up firefox and you should get internet access...

---

### Post by MaximB on 2006-05-16
no...in winxp I must enter correct username and password for my ISP
that's how it works
were can I type thouse in ubuntu ???

---

### Post by monchichi on 2006-05-16
ProjectGod, a lot of PPPoE providers do require authentication.

MAXDDARK, Install a program called "pppoeconf" and it will walk you through setting it up. In a terminal run:```
sudo apt-get install pppoeconf;sudo pppoeconf
```

---

### Post by mips on 2006-05-16
MAXDDARK, 

What adsl modem do you have, brand & model ???

It might be possible to get it to do the logon & pppoe stuff for you. then you just need dhcp on the pc.

---

