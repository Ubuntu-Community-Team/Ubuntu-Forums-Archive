---
title: "My strange connection prob"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-05-18
Hi,
I just installed Feisty 2 days ago on a new PC.  Everything went real fine.  Today I can't access the internet anymore.  Strangely only [www.gmail.com](www.gmail.com) and [www.google.com](www.google.com) could be accessed.  no other site could be browsed.  I am behind a DHCP router with 2 other computers; one with xp, the other which I'm using now has DSLinux and they are both working fine.  Thank you for any help

---

### Post by mendingo84 on 2007-05-18
interesting. maybe those 2 were in your cache. try a 
```

sudo /etc/init.d/networking restart
```

---

### Post by SteelCore on 2007-05-18
I tried that but still same situation. I don't think the 2 google site are from my cache because both pages are very recent.

---

### Post by SteelCore on 2007-07-12
I have finally found the solution to my connection problem at this thread ([http://ubuntuforums.org/showthread.php?t=410097&highlight=very+strange+networking+problem](http://ubuntuforums.org/showthread.php?t=410097&highlight=very+strange+networking+problem))
I currrently have to enter the code
```
sudo su
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```
at each start up.  I wonder if there is a way to make ubuntu automatically execute it.

---

