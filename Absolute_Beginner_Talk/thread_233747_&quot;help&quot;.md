---
title: "&quot;help&quot;"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by grey1 on 2006-08-10
:confused: 
New to Linux, and after having two computers wiped out from on-line-sicknesses,
need to know if there is a good firewall (type of) protection with my new Ubuntu 6.06 Dapper that is loaded on my new laptop or if there are extra programs to get for that help.

---

### Post by davebgimp on 2006-08-10
> **grey1 said:**
> :confused: 
New to Linux, and after having two computers wiped out from on-line-sicknesses,
need to know if there is a good firewall (type of) protection with my new Ubuntu 6.06 Dapper that is loaded on my new laptop or if there are extra programs to get for that help.

You can try firestarter:
**sudo aptitude install firestarter**

There's also Guarddog
**sudo aptitude install guarddog**

There's probably others, but either of those two will work fine.

---

### Post by A2A on 2006-08-10
Hi there and welcome to Linux, and the forums.
With linux, you typically do not need an AV software, however if you are running a mail server, and have this linux machine on a network (home?) where there could be other windows machines, you should get some AV protection.
Another reason to get an AV would be psychological, i.e: Peace of Mind :-)
I recommend Clam AV.  It's lightweight and not a hog on resources.  It's available via Synaptic, just search for ClamAV.
System -> Administration -> Synaptic Package Manager

Regards,
A2A

---

### Post by davebgimp on 2006-08-10
> **A2A said:**
> Hi there and welcome to Linux, and the forums.
With linux, you typically do not need an AV software, however if you are running a mail server, and have this linux machine on a network (home?) where there could be other windows machines, you should get some AV protection.
Another reason to get an AV would be psychological, i.e: Peace of Mind :-)
I recommend Clam AV.  It's lightweight and not a hog on resources.  It's available via Synaptic, just search for ClamAV.
System -> Administration -> Synaptic Package Manager

Regards,
A2A

The question was regarding firewalls.

---

### Post by xpod on 2006-08-10
Whats the story with clam av?...If you dont mind

i have it here but have read a couple of threads for how to get good old avg free edition.Im sure there were numerous reasons as to why this was apparently the better option OR was that just a piece of mind thing too?

I only access xp now and again but will be adding my kids pcs to our internet connection once i get the required hardware.

One will be an old m.e sys and one will be xp/ubunto and one will be kbunto

GOT the firestarter too

---

### Post by A2A on 2006-08-10
My bad, I guess I got too excited there :-(

Apologies to all hurt.

Regards,

A2A

Update:  By default Ubuntu is secure. What that means is that there are no open ports for an exploit to linger through.  Ports are opened when you install certain software, i.e: Apache, Webmin, etc...If you feel you need a firewall, davebgimp recommends firewire, and so do I :-)

---

### Post by A2A on 2006-08-10
> Whats the story with clam av?...If you dont mind

i have it here but have read a couple of threads for how to get good old avg free edition.Im sure there were numerous reasons as to why this was apparently the better option OR was that just a piece of mind thing too?

I only access xp now and again but will be adding my kids pcs to our internet connection once i get the required hardware.

One will be an old m.e sys and one will be xp/ubunto and one will be kbunto

If you have a faster machine you can use any AV you feel comfortable with.  To the best of my knowledge, ClamAV is free as well, and it runs faster than most, which results in a less lagged environment for your personal computing - Unless you have a really fast machine with at least a gig of RAM.

---

