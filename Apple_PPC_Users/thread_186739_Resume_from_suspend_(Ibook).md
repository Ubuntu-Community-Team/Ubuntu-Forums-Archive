---
title: "Resume from suspend (Ibook)"
date: 2006-06-02
forum: Apple PPC Users
---

### Post by Ford Flox on 2006-06-02
I'd like to first note that I'm running the live cd, I have not installed ubuntu yet. Suspend works fine by closing the lid, but opening it again does not successfully resume the computer. I can see some some diagnostics in the console, but then I get total darkness.

Perhaps it works better with a real installation. If so, tell me. Oh, and it's an Ibook G4, 1.2 GHz.

---

### Post by sulobanks on 2006-06-02
I have the same comp and I've been running Dapper on it since the RC came out. Still don't have sleep working correctly.  But I'm so happy that my external HD is recognized every time and my wireless works now that I hardly notice. ;)  I'll post if I get sleep/resume to work correctly.  I've noticed that if I'm at the login screen and shut the lid, it sleeps correctly and wakes correctly.  But if I'm logged in, it won't even go to sleep and if I leave it closed too long it just shuts down.

Edit:  BTW, I do remember sleep working perfectly when booted from the live cd.  But after a clean install, sleep only works when I'm not actually logged in.  I'm at a loss as to why this would be the case.

---

### Post by Ptero-4 on 2006-06-02
Hibernation support in iBooks have always been quite buggy.

---

### Post by farruinn on 2006-06-03
[quote=Ptero-4]Hibernation support in iBooks have always been quite buggy.[/quote]

Actually, hibernate is different from suspend. I think we're talking about suspend here (aka sleep on mac os) where the machine powers down but trickles a charge to the RAM. I haven't had these problems with my iBook G3, however hibernate (dump ram to disk) doesn't appear on my "quit" menu. I remember it appearing on an earlier livecd, but I dont' have the option now. Maybe I don't want it - I don't think it actually worked on the livecd, but my battery has gotten so bad it would be nice if this worked.

---

### Post by Ford Flox on 2006-06-03
[QUOTE=sulobanks]I've noticed that if I'm at the login screen and shut the lid, it sleeps correctly and wakes correctly.  But if I'm logged in, it won't even go to sleep and if I leave it closed too long it just shuts down.
[/QUOTE]
Have you made sure to enable suspend in the power management options? It's in one of the menus.

---

### Post by sulobanks on 2006-06-03
[QUOTE=Ford Flox]Have you made sure to enable suspend in the power management options? It's in one of the menus.[/QUOTE]

That was exactly it. It was set to blankscreen in GNOME. Oy! ](*,)   Can't believe I didn't think to look there.  I wasted so much time staring at pbbuttonsd.conf.  Thanks :)

---

### Post by David Oxland on 2006-06-03
I've got suspend troubles too; mine is a Dell Inspiron 9300.
If I select suspend from the shutdown menu or let it suspend due to inactivity it powers down but then won't come back with any key action.
Only key to get a response is power and then it comes up to a black screen and no key will change things. Only solution is to hold power button down for 10 seconds or more causing a shutdown and then to power up again.
After that operates as normal until I cause or allow a suspend again.

---

### Post by Tatey on 2006-06-12
The suspend function works correctly for me on my G4 iBook. I'd really like to be able to use hibernate though.

UPDATE: After resuming from suspend, Network Manager will not connect to a wireless network. Any idea's?

---

