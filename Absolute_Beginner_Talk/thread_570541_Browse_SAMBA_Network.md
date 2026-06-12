---
title: "Browse SAMBA Network"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-10-08
How do you browse a SAMBA network?  There doesn't seem to be any application like 'Network Neighborhood' or 'My Network Places' to view shared resources on your network?

---

### Post by Dr Small on 2007-10-08
Places > Network ?
But I always use:
```
smb://*ipaddress*
```

to access other computers over Samba.

Dr Small

---

### Post by mikeypc2006 on 2008-03-07
How would you browse a windows network through Xubuntu where the 'places' menu isn't an option?

---

### Post by NullHead on 2008-03-07
open up thunar I suppose. there is also PyNeighborhood ```
sudo apt-get install pyneighborhood
```

---

### Post by mikeypc2006 on 2008-03-07
> **NullHead said:**
> open up thunar I suppose. there is also PyNeighborhood ```
sudo apt-get install pyneighborhood
```

Thunar doesn't seem to have anything obvious unless I'm overlooking something?

---

### Post by rbc on 2008-03-08
I suggest the following. and this is based on help I got from the Forums:
Go to Synaptic and install Konqueror. When it's done, go to terminal and type "konqueror" (without the quotes). The window that appears will have a choice for Network folders. Click that. The next window will have a choice called Samba shares. Choose that, then your networked computers should show up. After i got it to work. Instead of going to terminal each time, I made a desktop launcher to launch Konqueror.

---

