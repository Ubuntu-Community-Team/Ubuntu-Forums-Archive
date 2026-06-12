---
title: "Wireless connection is too unstable."
date: 2006-09-20
forum: Apple PPC Users
---

### Post by Najand on 2006-09-20
I am using dapper on an iBook G4 and I am trying to
connect to the internet using wireless lan. I tried
set it up using the documentations but the connection
is so slow and unstable. (It sometimes connects to the
Internet and sometimes doesn't). 

It is the university wireless lan and with Mac OS X
and Ubuntu on i386, I get a reasonable fast connection.

I am not a Mac User, so I don't know much about the 
devices, etc. had been used in it. Does anyone have an
Idea? It would be great help. Thank you very much for 
your attention and I appreciate any helps in advance.

---

### Post by stmiller on 2006-09-21
Do you have gnome-network-manager installed? If not, install that.

And search this forum, esp in the wireless section.

[http://ubuntuforums.org/forumdisplay.php?f=139](http://ubuntuforums.org/forumdisplay.php?f=139)

And try setting to set the card with a 802.11b rate, which could be more stable:

$ sudo iwconfig eth1 rate 11M

(replace eth1 with whatever your wireless card is)

---

