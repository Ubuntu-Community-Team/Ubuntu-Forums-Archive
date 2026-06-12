---
title: "Linux crashing."
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by torx on 2006-01-31
So we all heard about Linux's immunity to crashes and microsoft BSOD-ing all the time. But, after my month long experience with Linux, i feel that this is not true at all.

We should stop lying to noobs and tell them honestly that linux is capable and does crash too.

Note: i am basing this on using Linux as a desktop computer, not as a server.

---

### Post by drfalkor on 2006-01-31
maybe you'r hdd is damaged ? Linux just can't crash by itself (or can it ?)

---

### Post by newuser111 on 2006-01-31
yes linux does crash but if your entire computer is locking up then there is something wrong with your setup or hardware

please provide more details

---

### Post by phillo660 on 2006-01-31
Hi Folks,
My ubuntu breezy crashes also randomly (as it appears to me).
Synaptic states that the packages linux-images-386 and linux-restricted-modules-2.6.12-10-386 are broken.
When I try to reinstall them I get the following error:

E: /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb: falló en buffer_write(fd) (10, ret=-1)

"fallo en buffer...":  "failed in buffer_write.. " (spanish)

What does that mean...?

Thanx for any help!!

---

### Post by mstlyevil on 2006-01-31
[QUOTE=phillo660]Hi Folks,
My ubuntu breezy crashes also randomly (as it appears to me).
Synaptic states that the packages linux-images-386 and linux-restricted-modules-2.6.12-10-386 are broken.
When I try to reinstall them I get the following error:

E: /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb: falló en buffer_write(fd) (10, ret=-1)

"fallo en buffer...":  "failed in buffer_write.. " (spanish)

What does that mean...?

Thanx for any help!![/QUOTE]

It looks to me to be a buffer overflow problem in your Internet cache file in firefox. Try increasing your cache limit in FF and try again.

---

### Post by christhemonkey on 2006-01-31
Things only crash for me when i do something stupid!
(like upgrading from hoary to breezy! :p)

---

### Post by phillo660 on 2006-01-31
but why do you suspect Firefox to be involved?:confused: 
I had 50 MB of cache for FF, now gave it 100MB, the problem is still the same

owner and group of /var is root, rwxr-xr-x permissions. that should not be the point.

ideas?

thank you!

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=drfalkor]maybe you'r hdd is damaged ? Linux just can't crash by itself (or can it ?)[/QUOTE]
Well, you can have a kernel panic.  That is basically your operating system saying, "AIYYYYEEEEE!!!!  I give up!"

It is usually caused by hardware problems.  User space applications aren't supposed to be able to force a kernel panic, though there have been bugs in the past that allowed that to happen.  QA on the kernel is usually very good, though.

---

