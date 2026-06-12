---
title: "Gnome and KDE wireless"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by natman on 2008-01-21
I use two wireless networks, home and school. In gnome things are ok i open up network manager and select the right network. I also have KDE and prefer it to gnome but the Knetwork manager simply is not working for me, i have to revert to using the Gnome app network manager in KDE each time, all i want is a start up app that guesses the right network.
Is it possible using both desktops has confused the apps, is there a way to start over with knetworkmanager ( without deleting the .kde dirc )

Thanks:

---

### Post by Kulgan on 2008-01-21
Not really familiar with KDE - I prefer Gnome :D
I think that getting rid of the related files in the .kde directory would be best - I'm not sure, since I got rid of KDE ages ago - but you shouldn't have to get rid of the whole directory. There should be some sort of logical hierarchy - but then again, it's KDE :P

With the Gnome network manager, I found that for some reason it helped to get rid of everything in the /etc/network/interfaces file exept the loopback lines, and let it write everything itself. That might be the case in knetworkmanager as well.

---

