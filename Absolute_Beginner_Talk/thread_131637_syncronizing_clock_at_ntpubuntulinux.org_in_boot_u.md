---
title: "syncronizing clock at ntp://ubuntulinux.org in boot up"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by Vega on 2006-02-16
I keep reading ntp:// instead of http:// when sycning with internet time. I get a fail every time I boot up my machine.

---

### Post by jimrz on 2006-02-16
not sure...maybe the site is down...mine did that both times i booted today, though it had never [at least that i noticed, but i don't use a splash screen and that bit of red is hard to miss] done before.

---

### Post by Mr X on 2006-02-16
[QUOTE=Vega]I keep reading ntp:// instead of http:// when sycning with internet time. I get a fail every time I boot up my machine.[/QUOTE]

ditto

---

### Post by rfruth on 2006-02-16
Count me as a [COLOR="Red"]fail[/COLOR] [COLOR="Black"] hopefully its just a temporary hiccup [/COLOR]

---

### Post by David Corrales on 2006-02-16
It fails because the network is not brought up properly before syncronizing so it can't reach the server.

---

### Post by linuxden on 2006-03-05
[QUOTE=Vega]I keep reading ntp:// instead of http:// when sycning with internet time. I get a fail every time I boot up my machine.[/QUOTE]


You get NTP, because it is not synching with HTTP (Hyper Text Transfer Protocol) it is synching with NTP (Network Time Protocol)... Its the protocol that makes us all have the same International atomic time... ;o) 

The reason why yours doesnt synch is because your network probs doesnt get setup on boot...(are you using PPP) 

Just a bit of geek info on NTP

[http://en.wikipedia.org/wiki/Network_Time_Protocol](http://en.wikipedia.org/wiki/Network_Time_Protocol)

Enjoy...

---

