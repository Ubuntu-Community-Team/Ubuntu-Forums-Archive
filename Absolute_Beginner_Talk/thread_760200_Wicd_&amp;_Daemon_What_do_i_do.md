---
title: "Wicd &amp; Daemon? What do i do?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Greenbean209 on 2008-04-19
Well I properly installed Wicd thats for sure, but it wont start. So i launched it in the terminal and it said daemon isn't running.
what is daemon, where do i get it, and is there anything else i might need to use Wicd?

---

### Post by eriqjaffe on 2008-04-20
The daemon mode is just part of the package, nothing extra to get.  What happens if you manually try starting the daemon?

```
sudo /etc/init.d/wicd start
```

---

