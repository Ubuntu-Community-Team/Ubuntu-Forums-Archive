---
title: "why do i have to nslookup to do anything outside of firefox?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by stonefeet on 2006-07-07
for example accessing/downloading repositories
i have to nslookup archive.ubuntu.com us.archive.ubuntu.com security.ubuntu.com and so on to be able to get them to work
it doesn't stop there
i even have to nslookup tracker addresses to get torrents to work

help, i've searched high and low and haven't found anything

---

### Post by mgor on 2006-07-07
hm, what the ..?

when you run nslookup, is it with or without the host parameter?
how does your /etc/resolv.conf look like?

---

### Post by stonefeet on 2006-07-07
yea, weird right?

i just do a simple nslookup address
no parameters
and then the repositories or torrent will come through
i have to do it just to connect to gaim too

resolv.conf
```
nameserver 192.168.1.1
```

this may help
the error i get without doing an nslookup is 101 network unreachable

---

### Post by deanlinkous on 2006-07-07
Sounds to me like something more than just a nameserver but where to start is a good question!

Have you tried setting your nameserver to a public one?

So you can browse the web fine just other stuff craps out on you?

---

### Post by IrishGangsta on 2006-07-07
Ok, lets work on my problem, i have posted like 3 threads and no one answers them.

I used Wine to download flashplayer 8

How do i use flashplayer 8 with my regular firefox browser or how do i use the Wine firefox my default browser?

---

### Post by stonefeet on 2006-07-07
> **deanlinkous said:**
> Sounds to me like something more than just a nameserver but where to start is a good question!

Have you tried setting your nameserver to a public one?

So you can browse the web fine just other stuff craps out on you?

yea i tried setting the nameserver to the one on the modem and yes the web works perfectly but everything else is a hassle.

i have dsl through linksys WRT54G router (all wired)
RealTek RTL8139 on the other pc
3com 3c905c (tornado) on this one

i had ubuntu on my other pc and it had the same problem as it is on this one, only torrents worked on that one just fine

---

### Post by T700 on 2006-07-07
> **IrishGangsta said:**
> Ok, lets work on my problem, i have posted like 3 threads and no one answers them.

I used Wine to download flashplayer 8

How do i use flashplayer 8 with my regular firefox browser or how do i use the Wine firefox my default browser?

[_http://www.ubuntuforums.org/showthread.php?t=82471_]("http://www.ubuntuforums.org/showthread.php?t=82471")

---

