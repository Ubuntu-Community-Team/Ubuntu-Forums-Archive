---
title: "Are my ports secure/closed?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-09-03
How can i scan which ports on my Ubuntu machine are open?
And if there have some... how can i close them?

---

### Post by ispmarin on 2006-09-03
You can start looking for open ports with

nmap -P0 -p 1-65335 <your ip>

to search for open ports. Usually, nmap will give you the name of the service that is running on that port. Look out for bittorrent/amule and similars, they usually uses high ports (around 4000). You can, then, close the ports shutting down the services that are open. 

hope it helps.

---

### Post by Blagomir on 2006-09-03
Well this helps, but now i have bigger problem. I have two open ports and in  the service field says "UNKNOWN". If i don`t know which service use this port, how to close it?

---

### Post by orb9220 on 2006-09-03
Also goto a site called shiels up and they will check how you are seen by  the internet. On default ports 22 or 23 and 80 are open.

---

### Post by Blagomir on 2006-09-03
My open ports are bigger than 1000. Not in 22,23,80.

---

### Post by ispmarin on 2006-09-03
Search in the net the the number of this ports, and try to see which service is running.  netstat is also your friend. Try to indentify the process id with netstat and the port corresponding from nmap. Do you have any internet program? Like gaim, skype, etc running?

---

### Post by Blagomir on 2006-09-03
All i have started is firefox. Nothing else which use internet. I reboot the system and now ports are change... is this possible to be some torrent tracker or something like that? I removed all torrent/amule client/servers form my synaptic, so i don`t think this is the problem but...

---

