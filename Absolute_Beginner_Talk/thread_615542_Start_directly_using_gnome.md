---
title: "Start directly using gnome"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by S.G. on 2007-11-17
I've tried to start gdm while having kdm in use and now when I start Ubuntu I have to write in a command window my username, password, and say sudo gdm start. 
How can I fix it? 

Thanks in advance

---

### Post by spiderbatdad on 2007-11-17
maybe...check out the options available under the tabs in System->Administration->Login Window.

---

### Post by spiderbatdad on 2007-11-17
sorry misunderstood your question. I think you can do Alt-F2 then metacity --replace

---

### Post by aktiwers on 2007-11-17
To make Gnome your default session, before you login at the login screen, pick Session and pick Gnome. Then log in and pick "make default session".

---

### Post by maybeway36 on 2007-11-17
Try
```
sudo dpkg-reconfigure gdm
```

---

### Post by S.G. on 2007-11-17
> **maybeway36 said:**
> Try
```
sudo dpkg-reconfigure gdm
```

Thanks a lot. It worked.

---

