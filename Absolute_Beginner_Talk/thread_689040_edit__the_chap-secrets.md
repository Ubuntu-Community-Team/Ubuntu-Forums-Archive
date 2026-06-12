---
title: "edit  the chap-secrets"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by manzoor on 2008-02-06
how to edit it ?

---

### Post by spiderbatdad on 2008-02-06
open it with a text editor using superuser privileges?```
gksu gedit /usr/share/ppp/chap-secrets
```

---

### Post by manzoor on 2008-02-06
its noot the /usr/share/ppp/chap-secrets

its the /etc/ppp/chap-secrets

---

### Post by spiderbatdad on 2008-02-06
us vi

---

### Post by spiderbatdad on 2008-02-06
```
sudo su
vi /etc/ppp/chap-secrets
```

---

### Post by manzoor on 2008-02-06
i used vi but it wont let me type in

---

### Post by spiderbatdad on 2008-02-06
mmm vi has two modes of use. command mode and insert mode. I believe hitting i will put you in insert mode. to get back to command mode hit esc. from command mode just enter :wq to save and quit.

You might want to take a quick look at a vi tutorial, but I believe that will get you started.

---

### Post by spiderbatdad on 2008-02-06
you may find nano much easier```
sudo su
nano /etc/ppp/chap-secrets
```

---

