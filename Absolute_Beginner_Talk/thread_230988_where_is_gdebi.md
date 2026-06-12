---
title: "where is gdebi?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by ieee488 on 2006-08-06
I downloaded the gnome-xxxx.deb file to my PC and copied it to my USB flash drive and took that flash drive to the laptop running Ubuntu.

I moved the  *.deb  file to the Desktop and double-clicked on it.
Archive Manager pops up. 

I want gdebi to run but it doesn't seem to be installed.

---

### Post by Fass on 2006-08-06
[http://packages.ubuntu.com/dapper/admin/gdebi](http://packages.ubuntu.com/dapper/admin/gdebi)

sudo aptitude install gdebi

Right click a deb file in nautilus and choose to have them always be handled by gdebi.

---

### Post by ieee488 on 2006-08-06
I don't have Dapper. I believe the CD that came with the book is Breezy 5.10. 

So, am I right to assume Gdebi won't work for me?  :(

---

### Post by 5-HT on 2006-08-06
Unfortunately, Gdebi is for Dapper.
Just install the .deb the conventional way: ```
 sudo dpkg -i /path/to/.deb 
```

---

### Post by ieee488 on 2006-08-06
thanks.

that's what I ended up doing.

---

