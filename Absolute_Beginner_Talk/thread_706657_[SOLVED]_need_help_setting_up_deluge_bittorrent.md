---
title: "[SOLVED] need help setting up deluge bittorrent"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by gandaran on 2008-02-24
I need some help here with the ports to open so that the deluge bittorrent client  will work correctly.
the deluge bittorrent doesn't download any torrent unless I open the 6881 port in firestarter firewall, but that isn't enough, it'll work only for a minute or two then stops.
anyone know how to set it up?

---

### Post by macogw on 2008-02-24
There aren't any ports closed in a default Ubuntu install.  Are you sure it's not the firewall built into your router that's the problem?

---

### Post by mivo on 2008-02-24
Have you set it to use random ports? It may be a problem with your ISP if you use the standard ports.

---

### Post by richaoj on 2008-02-24
it could be a router problem, but also alot of isps block torrents - try going in the settings and encrypting your connections.

---

### Post by S15_88 on 2008-02-24
open in deluge 6881 to 6889 and open those same ports in firestarter.
see if that helps...

Thanks, ALain

---

### Post by gandaran on 2008-02-25
problem fixed, I had all the ports blocked with firestarter, opening up from 6881 to 6889 did the trick.
thank you all.

---

