---
title: "not enough rights to save sources.list"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by secret_force on 2006-07-02
I want to adjust my sources.list as I added a wrong repository. When I open synaptic I get an error message saying that the repository is wrong, and this message is irritating, so I wanted to delete the repositor out of the list. However I can not save it as I don't have enough rights to do so. I don't get prompted with a box where i can type my password in, so I really don't know what to do to get enough rights. :confused:

---

### Post by Indras on 2006-07-02
Open up a terminal and type in:

```
sudo gedit /etc/apt/sources.list
```

It will ask you for your password, then open the file in Gedit with superuser privlidges.

---

### Post by taurus on 2006-07-02
Open a terminal with Applications -> Accessories -> Terminal and type
```

sudo gedit /etc/apt/sources.list

```

---

### Post by someusernoob on 2006-07-02
Open a terminal and type:

sudo gedit /etc/apt/sources.list

Now you will be able to save it when you removed the wrong repository

----

Lol, 3 posts all starting with: Open a terminal

---

### Post by Viper666 on 2006-07-02
u could also try:

sudo chown (your username) /etc/apt/sources.list

Now u can save the file. :p

---

### Post by jeremy on 2006-07-02
[QUOTE=Viper666]u could also try:

sudo chown (your username) /etc/apt/sources.list

Now u can save the file. :p[/QUOTE]
That isn't such a good idea. Do what was suggested in the earlier posts.

---

