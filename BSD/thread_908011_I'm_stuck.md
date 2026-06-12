---
title: "I'm stuck"
date: 2008-09-02
forum: BSD
---

### Post by swoll1980 on 2008-09-02
I got gnome installed. I had it running in the x session and it worked fine. then I add GDM to the rc.conf, restarted it gmd started up fine, but after I log in things start to go sour. It takes about 5 minutes to get from the GDM to the gnome desktop then once it's up and running it takes a good 2 minutes to open apps that I need. I restarted the computer, dropped down to a terminal, killed GDM, but it restarts automatically. I tried to start an x session, but now it wont let me. I tried to use the nano command to edit the rc.conf back to the way it was, but bsd doesn't know what nano is. Any advice?

---

### Post by Bachstelze on 2008-09-02
nano isn't installed in FreeBSD by default, you can use ee. And I can't help you with Gnome, sorry.

---

### Post by swoll1980 on 2008-09-02
> **HymnToLife said:**
> nano isn't installed in FreeBSD by default, you can use ee. And I can't help you with Gnome, sorry.

I used vi to change the file. I can start x sessions again gnome-panels plus all other apps run fine unless I try to start an actual gnome-session

---

