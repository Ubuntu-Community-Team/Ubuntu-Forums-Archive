---
title: "editing a text file?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-06-13
Im trying to edit  the text file "/etc/modules" but its not allowing me to. Iv tryed to replace it 2 and it says i dont have permissions! Is there any way to edit it from the command line logged in as root?

Thanks,
meniscus

---

### Post by frodon on 2006-06-13
If you want to edit it through nautilus run nautilus with root rights : ```
gksudo nautilus
```All the ubuntu partition need root rights to be edited (except your home directory), to edit the file in command line type that : ```
sudo gedit /etc/modules
```

If you don't know what is sudo you should read that : [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ProjectGod on 2006-06-13
:mrgreen: 

i prefer to use:

**sudo nano <file.conf>**

or 

**sudo pico <file.conf>**

more NEEERRRDY :D

---

### Post by meniscus on 2006-06-13
cheers frodon:D

---

### Post by ctgray on 2006-06-13
Wouldn't it be

gksudo nautilus --no-desktop

---

