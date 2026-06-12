---
title: "Command to Shutdown in Server"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by clarkth on 2006-05-21
All-

I installed ubuntu server and don't know the command to shutdown.  I tried sudo shutdown now, but I just get the root command line without a complete shutdown.  So what am I missing?  Thanks!

---

### Post by Klaidas on 2006-05-21
```
sudo shutdown -h now
```
The command line should stay for a few seconds and then the server shuts down

---

### Post by macdo on 2006-05-21
My personal favourite is ```
sudo poweroff
```
It seems so descriptive, somehow.

---

### Post by clarkth on 2006-05-21
Both of these work great.  Thanks a bunch.  :D

---

