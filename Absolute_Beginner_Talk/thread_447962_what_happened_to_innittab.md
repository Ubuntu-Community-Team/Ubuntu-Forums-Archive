---
title: "what happened to innittab?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by deerant on 2007-05-18
I'm not an experienced linux user (in truth i'm far from it) and i am learning mostly from generic linux documentation. So my question is How can i see what starts at each runlevel and how i can modify that? I couldn't find inittab nor a graphic tool for it. So how is the init order managed in ubuntu? Any help is welcomed.

---

### Post by Cypher on 2007-05-18
Ubuntu doesn't use the System V init system which relies on the /etc/inittab and other /etc/rcX files. It uses Upstart to manage system bring-up. Upstart supports the inittab file, but just to set the runlevel.

---

### Post by reacocard on 2007-05-18
> **Cypher said:**
> Ubuntu doesn't use the System V init system which relies on the /etc/inittab and other /etc/rcX files. It uses Upstart to manage system bring-up. Upstart supports the inittab file, but just to set the runlevel.

Exactly. 

Upstart config files are in /etc/event.d/, and backwards-compatibility is maintained with the /etc/rc*.d/ services as well.

As for managing it, just about all normal apps still use the system V symlink method, for which I recommend sysv-rc-conf. It's ncurses-based, but it works beautifully. Only the Ubuntu-specific stuff resides in the upstart config, which you'll have to edit by hand, but there isn't much of that so it shouldn't be an issue.

---

### Post by deerant on 2007-05-18
thanx!

i used sysv-rc-conf so the problem is solved

---

