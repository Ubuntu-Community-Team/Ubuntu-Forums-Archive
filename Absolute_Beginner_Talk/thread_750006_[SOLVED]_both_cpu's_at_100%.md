---
title: "[SOLVED] both cpu's at 100%"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Mick8882003 on 2008-04-09
Cant see a process that is causing it, wierd?
Any suggestions?

---

### Post by Tatty on 2008-04-09
System->Administration->System Monitor
Processes Tab
View->All Processes.

Try That.:)

---

### Post by Mick8882003 on 2008-04-09
The tabs are blanked and im not sure how to log in as su, when i switch user it gives me: the admin cant login from this screen

---

### Post by erginemr on 2008-04-09
It might be the tracker daemon (file indexer for faster search) working at the background.

Can you please install **htop**, which is sort of console equivalent of system monitor, with:
```
sudo aptitude install htop
```
and run it from the terminal with:
```
htop
```

---

### Post by Crafty Kisses on 2008-04-09
> **Mick8882003 said:**
> Cant see a process that is causing it, wierd?
Any suggestions?
You might also want to post your system specs.

---

### Post by Mick8882003 on 2008-04-09
fixed i used "top" to find out that it was boinc.

---

