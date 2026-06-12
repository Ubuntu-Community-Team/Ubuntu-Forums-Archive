---
title: "kde and wireless"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-11-17
hello,

i've decided to give kde a try, and installed in over my ubuntu edgy.  whenever i boot up and go directly to kde, my wireless doesn't work.  i have to exit the session, switch to gnome (whereupon wireless connects), then log back out and go back to kde- then it works.

what gives?  what info should i post?

thanks,

steve

---

### Post by wieman01 on 2006-11-17
Are you using Gnome-Network-Manager to connect to your wireless network?

---

### Post by stevieb on 2006-11-17
when using gnome, yes.  i think i've fixed the problem, though.  in kwifimanager, i went to the configuration editor (under settings) and entered my network name, told it to execute /sbin/dhclient on startup, and load preset configuration on startup.

seemed to work this time, anyway.  thanks for the replies!
-steve

---

### Post by msak007 on 2006-11-18
> **wieman01 said:**
> Are you using Gnome-Network-Manager to connect to your wireless network?

> **stevieb said:**
> when using gnome, yes.

Since you're already using NetworkManager in Gnome, why not use KNetworkManager in KDE instead of kwifimanager.
```
sudo apt-get install knetworkmanager
```

I use it and it works great.

---

### Post by stevieb on 2006-11-18
thanks!

i'm trying knetworkmanager now- it doesn't give me any options for wireless networks to connect to, despite being actively connected wirelessly (otherwise i wouldn't be posting this).

any ideas?  it looks like i don't need either knetwork or kwifi since i'm connecting anyway; i just like having it there in the tray to keep tabs on things.

thanks again for the reply,

-steve

---

