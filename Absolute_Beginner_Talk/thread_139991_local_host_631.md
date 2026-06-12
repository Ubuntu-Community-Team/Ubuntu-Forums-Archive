---
title: "local host 631"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-03-05
cannot access local host 631 therefore cannot install printer........... Any work around for this? or is it an IP issue?

---

### Post by jon_gunnar on 2006-03-05
[QUOTE=sailor2001]cannot access local host 631 therefore cannot install printer........... Any work around for this? or is it an IP issue?[/QUOTE]

What I did once in a time were this:

1)Adding the user "cupsys" to the group "shadow" will allow you to access [http://localhost:631](http://localhost:631)

2) sudo /etc/init.d/cupsys restart

[http://localhost:631/](http://localhost:631/)

A tip given by 
On Thu, 10 Nov 2005 06:37:06 +0000
Colin Murphy <lists@spudulike.me.uk> wrote:

---

### Post by sailor2001 on 2006-04-07
well. bought a new hp printer and was able to access localhost for cups and it install fast..HOWEVER... I rebooted to windows for a spell and then came back to ubunto. and no printer again...NOW i cannot access local host again for cups....Tried the user trick and nada............still stuck without a printer

---

### Post by sailor2001 on 2006-05-07
problem solved........Dlink wireless card was faulty.....even though I could go on line with it, it used so much resorces didn't have the power to start the printer. There was a few other problems also.......hot wiring to router and all is copesetic

---

