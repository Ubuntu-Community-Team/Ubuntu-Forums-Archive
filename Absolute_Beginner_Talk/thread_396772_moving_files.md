---
title: "moving files?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-29
hey all, i have some files that need to be put in certain folders that when i try to move them it says i dont have permission (example when i try to move a file to bin section in my filesystem i need permission to move it there).. i know theres a way to move files using terminal but how?

---

### Post by dbbolton on 2007-03-29
```
sudo mv /path/to/file /path/where/it/goes
```

(just a space between the location of the file and the location of the directory where you want to put it)

also, you can copy a file to a new location with 'cp' instead of 'mv'.
;)

---

### Post by noob_saioke45601 on 2007-03-29
alright thank you very much :)

---

### Post by Gordy on 2007-03-29
I'm not sure if this is a good way to copy and move files however, I use the terminal and enter sudo nautilus and of course it asks me for the root password. I now have permission to do what I need. Beware this can be very dangerous!!!!!

---

### Post by dbbolton on 2007-03-29
that's one way to do it. but if you want to launch a graphical app from the terminal as root, such as gedit, nautilus, etc, use gksudo:

```
gksudo nautilus / 
```

yes, it can be dangerous. but basically anything as root has the potential to be dangerous. don't mess with system files unless you know what you're doing.

---

