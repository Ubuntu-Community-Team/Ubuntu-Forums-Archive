---
title: "about  ubuntu server edition,,,,"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by determinedblkman1 on 2007-11-24
does the ubuntu server edition 7.10 have a gui ?

---

### Post by forestpixie on 2007-11-24
no it doesn't - if you want one you'll need to install ubuntu-desktop

```
sudo aptitude install ubuntu-desktop
```

---

### Post by banewman on 2007-11-24
Nope. :)

---

### Post by banewman on 2007-11-24
You can add GUI's after install with apt-get if that helps. :)
If you don't need a LAMP server you can use xubuntu and vnc as a file server on an old comp. :)

---

### Post by determinedblkman1 on 2007-11-24
the comp that i want to install it on isnt online, what do i have to download right now so that i can apply the gui (packages,etc.) later?

---

### Post by forestpixie on 2007-11-24
if it isn't online I would be inclined to get the whole download - you could end up with lots of unresolved dependencies I think.

---

### Post by daengbo on 2007-11-24
The easiest way is probably to download the (X/K)Ubuntu desktop CD, burn it, and put it into your server. Once there, login and type
sudo apt-cdrom add
This will add the cdrom's packages.
Then type 
sudo apt-get install ubuntu-desktop # Or kubuntu-desktop or xubuntu-desktop, depending on your preference.
The CD should have everything you need.

Cheers,
Daengbo

---

