---
title: "console firewall?"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by deerant on 2007-10-06
Is there a console firewall? Ncurses maybe? Or at least one that works remotely, so i don't have to make my own scripts?

---

### Post by jd65pl on 2007-10-06
See iptables, not for the faint hearted though!

---

### Post by deerant on 2007-10-06
> **jd65pl said:**
> See iptables, not for the faint hearted though!

I've seen it and that's what i am trying to avoid :)

---

### Post by HermanAB on 2007-10-06
The actual 'firewall' is the collection of netfilter kernel modules.  The main front end to that is called iptables.  *All* Linux firewall programs are simply scripts that run iptables commands.  Read 'man iptables' a few times then experiment a bit.  It will eventually make sense and some googling will help.

Cheers,

Herman

---

### Post by deerant on 2007-10-06
> **HermanAB said:**
> The actual 'firewall' is the collection of netfilter kernel modules.  The main front end to that is called iptables.  *All* Linux firewall programs are simply scripts that run iptables commands.  Read 'man iptables' a few times then experiment a bit.  It will eventually make sense and some googling will help.

Cheers,

Herman

Thanx Herman, however i already knew this and i'm trying to avoid writing my own scripts because learning to use iptables is a huge workload for me at the moment.

---

