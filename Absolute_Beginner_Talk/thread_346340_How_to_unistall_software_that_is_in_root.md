---
title: "How to unistall software that is in root"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by misfito on 2007-01-25
I wish to know how to unistall software that i installed in the root directory.
A couple of week ago I installed Wolfenstein ET but didn't work so I looked around 4 a solution and I found out that I installed it in root (the problem is I don't know how i dit it and what is root) I belive is in root because I looked on the properties of the carpet named .etwolf and it said owner:root permission:root, at the top. I tried to erase the carpet but I recieved a message that said that I don't have the permission.
please help :(

---

### Post by Happy_Man on 2007-01-25
All right: simply put the following command into your terminal:

```
gksudo nautilus
```

and navigate over to wherever you installed the file, and delete it. Remember to close the nautilus window afterwards, though! :)

---

### Post by misfito on 2007-01-28
> **Happy_Man said:**
> All right: simply put the following command into your terminal:

```
gksudo nautilus
```

and navigate over to wherever you installed the file, and delete it. Remember to close the nautilus window afterwards, though! :)
Thanx amigo

---

