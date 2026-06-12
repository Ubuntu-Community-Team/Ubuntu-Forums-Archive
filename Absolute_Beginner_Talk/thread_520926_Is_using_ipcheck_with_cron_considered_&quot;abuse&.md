---
title: "Is using ipcheck with cron considered &quot;abuse&quot; for dyndns?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by HautingLu on 2007-08-08
Hi,

I setup an SSH server with Feisty and setup a cron to run ipcheck every hour. But I'm still having issues with the IP constantly changing (b/c of no activity maybe?). 

Anyways, I started reading on dyndns.com:

> Updates should only be performed when your IP address has changed. We allow users to modify or "touch" their host every 28 days to prevent their hosts from expiring. Everything else is abusive.

Most write-up's I've been set the cron between 10min and 1hr. So I guess my question is **does ipcheck compare my ip before it sends it off?**

Ideally I'd like to go away for days and have access to it.

Thanks.

---

### Post by freebeer on 2007-08-08
I don't use ipcheck (I use ddclient), but assuming that ipcheck does the same thing as ddclient, you should be fine.  ddclient only changes your dyndns entry IF your ip address has changed.  In other words, there's a check to see if the IP addy has changed.  If it hasn't, nothing is done (dyndns isn't contacted).  Since dyndns offers up both scripts, I think it's safe to assume that these scripts pass their "abuse" test. :D

---

### Post by HautingLu on 2007-08-08
> **freebeer said:**
> I don't use ipcheck (I use ddclient), but assuming that ipcheck does the same thing as ddclient, you should be fine.  ddclient only changes your dyndns entry IF your ip address has changed.  In other words, there's a check to see if the IP addy has changed.  If it hasn't, nothing is done (dyndns isn't contacted).  Since dyndns offers up both scripts, I think it's safe to assume that these scripts pass their "abuse" test. :D

I did see ddclient as a suggested client. Is ipcheck also "recommended" by them?

---

### Post by HautingLu on 2007-08-09
Can anyone confirm that ipcheck is "abuse friendly" for dyndns? :razz:

---

### Post by eentonig on 2007-08-09
No idea about ipcheck.

But I also use ddclient. My box is behond a NAT router, so It checks every hour on their webserver what the current public IP is, and updates it only when necessary.

I never had a complaint about abuse.

---

### Post by MenZa on 2007-08-09
I like to use ez-ipupdate; it has a nice, user-friendly way of configuring itself.

```
sudo apt-get install ez-ipupdate
```.

---

### Post by HautingLu on 2007-08-09
> **MenZa said:**
> I like to use ez-ipupdate; it has a nice, user-friendly way of configuring itself.

```
sudo apt-get install ez-ipupdate
```.


Ahhhhhhhhhh where were you two weeks ago! :mrgreen::mrgreen:

Exactly what I was looking for. But a question, how often does it update itself? Because it seems like 1hr is too long for me.

Thanks.

---

### Post by MenZa on 2007-08-09
It updates itself whenever you change your IP. It continually monitors whatever network interface you specify.

---

### Post by HautingLu on 2007-08-09
> **MenZa said:**
> It updates itself whenever you change your IP. It continually monitors whatever network interface you specify.

Thank you! :)

---

### Post by HautingLu on 2007-08-10
OK new problem. Seems like ez-ipupdate see's my IP as 192.28.0.XXX and not my router IP. 
Back to square one.......is there something I'm missing?

---

### Post by freebeer on 2007-08-11
> **HautingLu said:**
> I did see ddclient as a suggested client. Is ipcheck also "recommended" by them?

My bad.  It's another script by a different name.  (Memory can be a bad thing on which to rely.) :)

Have you tried ddclient?  It seems that the consensus is that other folks are having success with it.  I recall that it was pretty easy to set up.  Although I don't use it, ddclient has a feature that might solve your router IP addy problem.  (IIRC, it'll work with ipcheck(?) to check your "outside" IP, then contact dyndns IF your addy has changed.

---

### Post by HautingLu on 2007-08-11
I just instaleld ddclient but it still updates my local ip instead of the external one....192.xx.xxx

Any ideas? :confused:

**EDIT:**

Problem solved:

Commented out:
> 
## via hardware interface (if you don't have a router/firewall)
#use=if, if=eth0

and added it: 
> 
## via our CheckIP server
use=web, web=checkip.dyndns.com/, web-skip='IP Address'

---

### Post by freebeer on 2007-08-11
> **HautingLu said:**
> 

Problem solved


Cool!  [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG]

---

### Post by cookfromfrozen on 2007-08-17
i don;t know why but one of my dyndns clients was "touching" the dyndns server about every 10 minutes for nearly a day.  nothing ever happened, i still have my dyndns

---

