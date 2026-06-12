---
title: "Clamav"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-27
I get this error:

```
Warning: No virus definitions found! If you are sure you have definitions installed, please inform the developer where your definitions are held so the paths can be added.
``` on start up of ClamAV.


How do I install definitions?

---

### Post by billgoldberg on 2008-03-27
Go to "system -> preferences -> synaptic package manager".

Click on search and type in 'clamav'.

You should have the following packages:

[[img]http://xs125.xs.to/xs125/08134/clam546.png[/img]](http://xs.to)

The third one will get the definitions from the web.

-----------

You do know that clamav only scans for windows viruses eh?

So unless you are on a network with other windows pc's, it's useless for you linux pc and will only slow it down.

---

### Post by Tom--d on 2008-03-27
Ah.. I see.

So there is no point in having it?

---

### Post by Kevbert on 2008-03-28
It looks like clamav / clamtk loads files on boot-up.  Is there antivirus software for linux which doesn't  ?  According to clamtk I've had four Windows viruses so far.  As I used a shared Windows data drive won't this cause problems ?
I have separate antivirus / rootkit / malware software for Windows.

---

