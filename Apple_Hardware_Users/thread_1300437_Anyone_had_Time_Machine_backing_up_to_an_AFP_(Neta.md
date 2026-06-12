---
title: "Anyone had Time Machine backing up to an AFP (Netatalk) volume in Snow Leopard?"
date: 2009-10-25
forum: Apple Hardware Users
---

### Post by wesg on 2009-10-25
I bought another TB drive today with the intention of setting up Time Machine backups for my MacBook. I followed the steps to display network volumes in Time Machine, but have now hit a stone wall.

I did the sparsebundle tricks, and even added the plist file. Nothing has worked so far, probably because all the other users I read about were using a USB drive connected a computer or Airport Extreme. 

Has anyone gotten Time Machine backing up to a Ubuntu-powered AFP volume? I'm curious about what you're doing that I'm not...

---

### Post by tiresia on 2009-10-25
I have a PPC running Leopard 10.5 so I'm just talking without any personal experience... I think that Leopard Snow does not support AFP, ie AppleTalk is not working anymore in Leopard Snow
[Here]("http://discussions.apple.com/thread.jspa?threadID=2132899&tstart=0") is a thread about this issue (but referred to AppleTalk Printers connected to a Leopard Snow Machine)

---

### Post by dmovad on 2009-10-28
FYI, the preferred protocol for Apple network shares is still Apple Filing Protocol (AFP).  Appletalk is completely different and sort of like a "wired" version of Bonjour and is NOT supported in Snow Leopard.

---

