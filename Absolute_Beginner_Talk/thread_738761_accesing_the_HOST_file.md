---
title: "accesing the HOST file"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by daberger on 2008-03-29
in windows xp i could easily edit the HOST file and block some advertisements on sites that i often visit. does any1 know how i can access it?
ty i run hardy

---

### Post by Tatty on 2008-03-29
I think you might be looking for /etc/hosts

---

### Post by daberger on 2008-03-29
maybe i am. how do get to that?

---

### Post by Tatty on 2008-03-29
Well you will need to open it in a text editor with root privilages, so open a terminal (Applications->Accessories->Terminal) then type this:

```
gksudo gedit /etc/hosts
```

---

### Post by Locutus_of_Borg on 2008-03-29
```
sudo gedit /etc/hosts
```

too slow...and apparently i cannot delete my own posts?

---

### Post by daberger on 2008-03-29
my thanks to u

---

