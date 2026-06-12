---
title: "Internet, ports, programs, torrents.. how to stop this?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-04-28
Hi. I have shared my internet connection from my UBUNTU to my WINBOZE machine. But how can i allow my WINBOZE machine to use unly web, icq, chat and some other programs, but not to use torrent clients?

---

### Post by mostwanted on 2006-04-28
I guess you could set up a firewall like Zone Alarm to only allow those programs to connect to the Internet. And not let everyone have administrator privileges so that they can install software themselves.

---

### Post by Blagomir on 2006-04-28
I have no access to my win machine for the moment. How can i stop/allow this programs to connect to Internet via my UBUNTU machine?

---

### Post by mostwanted on 2006-04-28
[QUOTE=Blagomir]I have no access to my win machine for the moment. How can i stop/allow this programs to connect to Internet via my UBUNTU machine?[/QUOTE]

lol, that's an odd request :)

I really wouldn't know, but you probably can't do something like that.

---

### Post by Blagomir on 2006-04-28
Is there any way to allow my win machine to connect only on specified ports, and to disallow others in my ubuntu ?

---

### Post by steve.horsley on 2006-04-28
I think that firestarter is the most commonly recommended firewall for Ubuntu in these forums. I haven't used that much - just looked at it once. If firestarter doesn't give you enough flexibility, you could try guarddog instead. I have used that quite often, and I like it. 

Both firestarter and guarddog are in the repositories.

---

### Post by Blagomir on 2006-04-28
I just installed Firestarter, but i don`t see option to block some ports.

---

### Post by louis_nichols on 2006-04-28
Ports that are forwarded through your pc are in firestarter under inbound connections/forwarding. There, you should choose a restrictive policy and only enable ports you want.

---

