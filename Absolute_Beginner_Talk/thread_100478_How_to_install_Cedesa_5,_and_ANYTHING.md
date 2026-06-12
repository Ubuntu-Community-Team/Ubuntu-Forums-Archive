---
title: "How to install Cedesa 5, and ANYTHING"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by shahid_2dk on 2005-12-07
How do I install Cedesa 5?
How do I install anything, Synaptic cant find the manually downloaded files.

How does a packet file end? (extensien?)

Ive just installed Empire Earth with Wine 0.92, installed in the standard folder with wine, c: etc., how do i then start the game? "wine what to write here?"

Thx for any help in advance ;)

Now I am off to bed =;

---

### Post by aysiu on 2005-12-07
[QUOTE=shahid_2dk]How do I install Cedesa 5?[/quote] I don't know.

> 
How do I install anything, Synaptic cant find the manually downloaded files. Synaptic downloads from repositories. You don't need to manually download.

> 
Ive just installed Empire Earth with Wine 0.92, installed in the standard folder with wine, c: etc., how do i then start the game? "wine what to write here?" Probably something like this ```
wine "z:\home\shahid\.wine\drive_c\Program Files\Empire Earth\Empire.exe"
```

---

### Post by lleb on 2005-12-07
to install cedega after you have downloaded it, you sudo dpkg -i cedega.deb and away you go.

any .deb package should be done that way. you have to be root level to run dpkg

---

