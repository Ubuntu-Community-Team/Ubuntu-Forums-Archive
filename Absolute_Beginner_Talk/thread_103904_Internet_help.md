---
title: "Internet help"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by neoltlink on 2005-12-15
Alright, I'm dual-booting ubuntu and windows xp.
When I go into windows I can go online fine, but on linux it has no connection.
Putting the qwest installation cd in wont help, it's for windows and mac only.
I'm using a Qwest Actiontec DSL modem. 
There is probably a simple solution to this, but i've searched around and couldn't fine anything.
Any help is appreciated...:)
Oh, and wierd thing is, I downloaded the updates for it fine. Just can't surf web/IM/email, anything like that.

---

### Post by monchichi on 2005-12-15
[QUOTE=neoltlink]Alright, I'm dual-booting ubuntu and windows xp.
When I go into windows I can go online fine, but on linux it has no connection.
Putting the qwest installation cd in wont help, it's for windows and mac only.
I'm using a Qwest Actiontec DSL modem. 
There is probably a simple solution to this, but i've searched around and couldn't fine anything.
Any help is appreciated...:)
Oh, and wierd thing is, I downloaded the updates for it fine. Just can't surf web/IM/email, anything like that.[/QUOTE]

That is weird. Is it aDSL? If so, you probably need to authenticate using pppoe.
Try running pppoeconf and setting it up.

---

### Post by neoltlink on 2005-12-15
Although I'm pretty sure it isn't aDSL, i tried that anyway.
Didn't work, after it scanned it said"Detected one ethernet device "eth0".But, after that, it said something along the lines of "Sorry, but this connection couldn't be authenticated,"or something like that.
Any ideas?

---

### Post by monchichi on 2005-12-15
hmm... are you given an legitimate ip address? run 'ifconfig' in a terminal to check.

can you access the firmware on the modem? (by pointing your browser to [http://192.168.0.1](http://192.168.0.1) or whatever it is)

try running the following in a terminal also:```
sudo ifconfig eth0 up
sudo dhclient
```

---

### Post by neoltlink on 2005-12-16
Alright, I tried that. Now I can connect to a few websites, such as these forums, but not google, antiproxy.com (was gonna try to use a proxy), and nearly all others.

---

### Post by neoltlink on 2005-12-16
Teh bump

---

### Post by Mustard on 2005-12-16
I'm shooting in the dark here, as I don't use DSL, but...

Would it be a problem with DNS servers?

What do you get when you do this..... cat /etc/resolv.conf   ?

---

### Post by neoltlink on 2005-12-16
Doubt it would be, seeing as I can connect to some sites, using their domain names, but I'll try it. 
Thanks! :)

---

### Post by Mustard on 2005-12-16
[QUOTE=neoltlink]Doubt it would be, seeing as I can connect to some sites, using their domain names, but I'll try it. 
Thanks! :)[/QUOTE]

Yeah...well as I say...I'm shootin' in the dark.  You just looked a bit lonely with your problem going down the page and needing to be bumped. :)

I'm on dialup myself, and networking has always been a bit of a mystery to me.

---

