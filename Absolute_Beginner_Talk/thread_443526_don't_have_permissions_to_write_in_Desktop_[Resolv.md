---
title: "don't have permissions to write in Desktop [Resolved]"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-05-14
only root can do it. How can i set it to give permission to all users?

---

### Post by Dr Small on 2007-05-14
Log on as root, right click on the desktop folder, (located in /home/me/) and go to properties. 
Permissions > File Owner and File Group. Change that to your username.

Dr Small

---

### Post by Pulka on 2007-05-14
can't login as root

---

### Post by lazyart on 2007-05-14
```
sudo chown -R username /home/username
```

That should make you the owner of your home directory and let you do what you want.

---

### Post by aysiu on 2007-05-14
Paste lazyart's command into [the terminal](http://www.psychocats.net/ubuntu/terminal).

---

### Post by Pulka on 2007-05-14
done. thank you

---

