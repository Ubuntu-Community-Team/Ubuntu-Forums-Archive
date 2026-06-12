---
title: "Making all ports stealth"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Zennlavian on 2007-08-04
I recently ran the Sheilds Up! test at grc.com.

Results from scan of ports: 0-1055

    0 Ports Open
 1049 Ports Closed
    7 Ports Stealth
---------------------
 1056 Ports Tested

My question is: how do I make all ports stealth?  I only passed 2/3 of the tests.  I have enabled ICMP filtering in firestarter.  It was my understanding that all ports were stealth by default.  I have configured my router to the highest level of security.

---

### Post by Aurdal on 2007-08-04
All ports are closed by default.

---

### Post by Zennlavian on 2007-08-04
thanks for the reply.

> **Aurdal said:**
> All ports are closed by default.

well, is there anyway to make them all stealth?  I have read some previous threads where ubuntu users passed this test.

---

### Post by quibbler on 2007-08-05
> **Zennlavian said:**
> thanks for the reply.



well, is there anyway to make them all stealth?  I have read some previous threads where ubuntu users passed this test.
Hi Zennlavian,

I,m using the firewall " Firestarter", and everything is stealth.
It is very easy to setup. Install from Synaptic.

Regards
Quibbler

---

### Post by nitro_n2o on 2007-08-05
if you want some super easy visual way to control your pc get webmin.. it needs php and apache though
```
sudo apt-get install php5 apache2 libapache-mod-php5 webmin
```

---

### Post by Zennlavian on 2007-08-05
I'm sorry I abandoned this thread, but I had an emergency.

My question still remains: how can I make all ports stealth on ubuntu?  I'm running a dual hd system with XP.  When I ran the Sheilds Up! test on XP, all ports were stealth.  I am running ZoneLabs.

I also configured my router (Actiontec DSL Gateway GT704).

---

### Post by smah77 on 2007-08-05
Weird mine were all stealth by default.  Maybe yours aren't because of some services you're running or something?

---

### Post by FleetAdmiral74 on 2007-08-05
> **Zennlavian said:**
> I'm sorry I abandoned this thread, but I had an emergency.

My question still remains: how can I make all ports stealth on ubuntu?  I'm running a dual hd system with XP.  When I ran the Sheilds Up! test on XP, all ports were stealth.  I am running ZoneLabs.

I also configured my router (Actiontec DSL Gateway GT704).

What do you mean the question remains? Someone already answered you above, have you read the posts?

And the ports are stealthed with me as well by default, are you using any unusual network software already?

---

### Post by Zennlavian on 2007-08-05
Thanks for the replies.  I now believe that it has something to do with my router configuration.  The reason that the ports are stealth on XP is due to ZoneAlarm.  I am googling now trying to find a way to configure my router.

---

