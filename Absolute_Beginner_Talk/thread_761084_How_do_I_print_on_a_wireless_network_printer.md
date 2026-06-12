---
title: "How do I print on a wireless network printer?"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by gatorbrit on 2008-04-20
I run ubuntu on my wireless laptop.  My desktop runs windows vista (yuck).  The Canon printer is connected to the windows computer.

Can I print wirelessly from my laptop to the printer easily - or is that something that would take a lot of work?

Thanks

R

---

### Post by joshrobinson on 2008-04-20
its not to hard, as long as ubuntu can use the printer correctly

you need to go on the vista pc, and share the printer, and change all the share options to be able to accept guest connections and no passwords, then restart the vista machine

use synaptic, install samba, and edit this file to match your workgroup name on windows
```
sudo gedit /etc/samba/smb.conf
```

then use the printers app in system > administration > printing
new printer, samba printer, then browse to the windows pc's printer, pick a driver and try a test page

---

### Post by gatorbrit on 2008-04-20
Fantastic - I'll try it right now!!! 

Thanks

---

### Post by DXM31 on 2008-04-20
That all works except when I try to print something.
The printer icon shows up and just sits there and sits there...
It doesn't print???
OBTW it worked in Mandriva Spring on my other laptop first try.

---

