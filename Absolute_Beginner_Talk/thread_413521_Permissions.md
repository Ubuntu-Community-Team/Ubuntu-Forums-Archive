---
title: "Permissions"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2007-04-19
Hi all,   I want to completely remove a program I complied  I go to PLACES--Search for files and find all instances of a filename.  When I try to remove them, I get a msg. saying I don't have permission to remove them.  How do I change the permission in the command line.. or elsewhere...so I can delete these files ???   I've read stuff and don't seem to find it .

---

### Post by meborc on 2007-04-19
you can start up nautilus in root mode```
sudo nautilus
```- from terminal

but be careful... you now have permission to delete everything if you liked... yes, i said EVERYTHING :)

---

### Post by MrKlean on 2007-04-19
thanks, I'll keep that in mind, but it wasn't what I needed.  I was referring to the search for files... under PLACES in the panel.  I hope I made it clearer ; )

---

### Post by sisco311 on 2007-04-19
in terminal:
```
sudo gnome-search-tool
```

---

### Post by MrKlean on 2007-04-19
Sisco, that gets me closer, but I can't do a search on filesystem...only on root, desktop and my name. Any thots would be appreciated ; )
Thanks !

---

### Post by sisco311 on 2007-04-19
Look in folder -> Other...
click the Type a filename icon (it's in the upper left corner )
and type /
(slash) for Location

---

### Post by MrKlean on 2007-04-19
sisco, thanks for the learning experience!  One question, why do some files say they don't exit when I try to remove them ???   It shows them, but says they don't exist LOL!!
Thanks ; )

---

