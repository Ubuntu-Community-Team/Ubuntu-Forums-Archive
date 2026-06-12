---
title: "what are the exact steps i would need to take to switch to my other video card?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-07-05
currently, I have an ati radeon 7500 64MB video card installed on my dapper desktop.  when i installed dapper, it gave me no errors, so obviously it likes the card.  i also happen to have an ati radeon 9800 pro 128MB lying around, and i thought i might replace my old card with this newer one.  i havent messed with drivers of any kind, i've never downloaded one driver for my graphics card. 

So, what would I need to do to get my radeon 9800 pro running and what driver would i need to get (if any)???

---

### Post by scxtt on 2006-07-05
IMO, you can switch out cards w/ NO issue ... check out your /etc/X11/xorg.conf file and see what "Driver" it's using (most likely vesa or ati, maybe radeon) ... then check out the link in my sig to get fglrx working for your 9800 ...

```
:> cat /etc/X11/xorg.conf | grep Driver
```

---

### Post by user1397 on 2006-07-05
[quote=scxtt]IMO, you can switch out cards w/ NO issue ... check out your /etc/X11/xorg.conf file and see what "Driver" it's using (most likely vesa or ati, maybe radeon) ... then check out the link in my sig to get fglrx working for your 9800 ...

```
:> cat /etc/X11/xorg.conf | grep Driver
```[/quote]its using the "ati" driver.  isn't that howto in your sig only for X??? series cards, not 9??? series cards?

---

### Post by scxtt on 2006-07-05
good point - i was "sure" it works w/ X??? series cards - but yours, being a 9800, should be ok to have it work ... basically it's for any card that **can** make use of fglrx drivers - ati's page shed's light on that, saying "RADEON 8500 Series and higher" ... it should work fine for you ... again, this does basically assume either a fresh install or that you've NEVER attempted driver install before ...

---

### Post by user1397 on 2006-07-05
[quote=scxtt]good point - i was "sure" it works w/ X??? series cards - but yours, being a 9800, should be ok to have it work ... basically it's for any card that **can** make use of fglrx drivers - ati's page shed's light on that, saying "RADEON 8500 Series and higher" ... it should work fine for you ... again, this does basically assume either a fresh install or that you've NEVER attempted driver install before ...[/quote]well i've never attempted drivre install before, so i guess im good.  thanks for the link man

---

### Post by scxtt on 2006-07-05
it **really** made my day when i found it and it worked - i'm glad to pass it on ... i hope it works as flawlessly for you as it does for me ...

---

