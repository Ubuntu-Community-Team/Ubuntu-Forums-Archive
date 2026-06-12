---
title: "Can't remote admin CUPS - &quot;Unable to Connect&quot;"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by SparkyFlooner on 2006-08-19
I'm unable to admin CUPS remotely.  When I try to connect, my browser tells me "Unable to Connect".

I'm running a pure server..no X server.  Any ideas?

I've added cupsys to group shadow and all that...nothing.

---

### Post by GeekSpeek'r on 2006-08-19
are you running through a router/firewall to remote manage? If so, you need to allow incoming UDP port 631 to the cups server box. Also insure that your cupsd is running

---

### Post by TFX360 on 2006-08-19
> **SparkyFlooner said:**
> I'm unable to admin CUPS remotely.  When I try to connect, my browser tells me "Unable to Connect".

I'm running a pure server..no X server.  Any ideas?

I've added cupsys to group shadow and all that...nothing.

Under Administation/Printers klik one of the tabs. There you can open the port on your pc. It isn't open standard.

Kind regards,


TFX

---

### Post by SparkyFlooner on 2006-08-19
This is all inside a LAN, hidden behind a router that's directly connected to the internet.

With no firewall on the client or server, I still can't load the admin page.

I verified cupsd is running.

And X isn't on my server.  I admin through ssh.

---

### Post by SparkyFlooner on 2006-08-19
bump

---

### Post by SparkyFlooner on 2006-08-20
bump

---

### Post by ?@yk0&amp;^4 on 2006-09-05
I had the same problem.

After doing the useradd stuff, you need to edit /etc/cups/cups.d/ports.conf - change 'Listen localhost:631' to 'Listen 10.0.0.*:631' (or whatever address for your network).

I then edited /etc/cups/cupsd.conf - changed all 'Allow @LOCAL' to 'Allow 10.0.0.*'.
 
Then restart cups daemon.

Sorry this is very brief, I'm tired. If you need further explanation, let me know!

Thanks,
Greg.

P.S. I think at some point you might need to get into the interface and enable remote admin too, can't remember exactly...

---

