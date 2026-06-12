---
title: "Root user problem"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-03-12
I've been trying to modify my Sources.list file for the past few minutes now, and when I try to save, the file says that I cannot because I do not have access to. I've tried logging in as root, but that doesn't seem to work. I'm using Kubuntu now, by the way.

---

### Post by Del Boy on 2007-03-12
```
sudo nano /etc/apt/sources.list
```

Should work...

---

### Post by Tipo on 2007-03-12
It just means that you need to have super user priviledges.

try following the steps here: [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

The major thing here is the use of the command 'sudo', it will then ask for your password, enter it, and you will have superuser priviledges

---

### Post by aysiu on 2007-03-12
Tipo's right on for that particular task.

In general, though, you may want to read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

