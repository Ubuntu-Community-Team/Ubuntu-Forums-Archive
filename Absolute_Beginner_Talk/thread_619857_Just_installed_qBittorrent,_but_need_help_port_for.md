---
title: "Just installed qBittorrent, but need help port forwarding..."
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-11-21
Hi,  

I just installed qBittorrent.  How do I get Firestarter to forward to Port #35,000, for example, since this is the Port that I tell my DSL router to open for incoming connections when running utorrent in Win XP?  As it is now, when I left click on Policy then right click on Allowed Service > Bittorrent, I only see the default Port Range 6881-6889.  I also entered the following in the terminal but nothing happens:

sudo iptables -A INPUT -p tcp --dport 35000 -j ACCEPT

Any suggestions?  Thank you.

---

### Post by Inxsible on 2007-11-21
In Firestarter, you can forward ports. Just change the port to 35000 and it will automatically change the name to Unknown. You can even change the name if you like

---

### Post by iClouseau88 on 2007-11-22
Hi,

qBittorrent doesn't work for ports other than the defaults, namely Ports 6881-6889(?).  I had to revert to Bittorrent and Ports 6881... and this worked.

---

