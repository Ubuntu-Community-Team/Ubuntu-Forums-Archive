---
title: "Ubuntu box keeps dropping wireless connection"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Monsieur le Comte on 2007-01-21
I have my ubuntu box connected to our network via a wireless card.  I have SSH and HTTP services running on it.  However, after it sits for maybe a day or so it always loses the connection.

Ifconfig tells me that it still has an IP address, and the gnome network connection program SAYS that the wireless card is enabled, but I cannot ping the box from another computer, nor can the ubuntu box itself ping any other computer.

Basically it looks like the wireless card is going inactive after a while and it requires a reboot to fix.  Disabling and re-enabling the card doesn't work.

I checked my power management settings to make sure it wasn't set to sleep and it isn't. I'm running out of ideas as to what could be the problem.  Any takers?

---

### Post by Sniper99 on 2007-01-21
i am having the same kind of problems.......i just do a total reconfig of everything....i cant help you much after that...sorry...but i have found that it may be a router issue, cuz my psp can connect to it, but all the other comps in the building have a very finicky connection.....maybe try a different router

---

### Post by moshuptrail on 2007-01-21
Could it be that the DHCP lease has expired and it's not renewing correctly?

---

### Post by Monsieur le Comte on 2007-01-21
> **moshuptrail said:**
> Could it be that the DHCP lease has expired and it's not renewing correctly?

I almost thought that but then I remembered that I have the ubuntu box set up as static outside of the DHCP range.

---

### Post by BigCommieNat on 2007-11-21
Same issue here... I've replicated this across two boards, one nividia, one via.

the only thing I've noticed is that this tends to happen sooner after the restricted Nvidia graphics drivers are installed... either way, it's annoying

---

### Post by Shrynn on 2007-11-21
I also have this issue. Started out this happened like once a week. Now I've just had it happen twice today.. I also have Nvidia Graphics driver installed. Dunno if that is the issue or not but this really is annoying..... 

Anybody with an idea?

---

### Post by OffAxis on 2007-11-21
I was having a similar issue with my wireless dropping out. Last week it starting dropping every time I tried to run apt-get. It would kill my entire connection (wired, too) and I would have to release/renew my wan IP at the router.

I changed my router out yesterday, successfully ran apt-get wirelessly, and it hasn't dropped out again (yet).

So you might start there like Sniper99 suggested.

---

### Post by OffAxis on 2007-11-21
> Same issue here... I've replicated this across two boards, one nividia, one via.
were you using the same router?

---

### Post by Sniper99 on 2007-11-25
i know that this is waaaay late..but yeah..we got wirless extender..and that seemed to put the problem to bed..i have since fried my ubuntu box..so i have no other things to say from there..i also had installed those drivers..maybe its a mixture of the two

---

