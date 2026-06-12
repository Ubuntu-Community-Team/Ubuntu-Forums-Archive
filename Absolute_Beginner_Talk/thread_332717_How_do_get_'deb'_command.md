---
title: "How do get 'deb' command"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by chapmc on 2007-01-06
I found a thread about installing canon printer driver and instructions say use command

deb [http://.](http://.).........

I get a command not found.

What do I need to install to be able to do this?  I am using edgy.

Thanks.

---

### Post by CroEragon on 2007-01-06
i know you are missing one command before deb but dont know wichone.

---

### Post by Bachstelze on 2007-01-06
Lines beginning with deb and then a URL are not comands but lines you need to add so the APT sources file. Open it in your favourite text editor, e.g. :

```
sudo nano /etc/apt/sources.list
```

then paste the line in it, save the file (Ctrl+O, Enter to confirm), exit nano (Ctrl+X), and run

```
sudo apt-get update
```

---

### Post by inveratulo on 2007-01-06
To add to what Hymn has already said, the driver instructions might want you to enable universe and multiverse source listings.  Details found here:
[http://wiki.arslinux.com/Ubuntu#Edgy_.286.10.29](http://wiki.arslinux.com/Ubuntu#Edgy_.286.10.29)

i made a backup copy of the original source.list and just created a new one with the above information in it.  don't forget to sudo apt-get update



good luck

---

