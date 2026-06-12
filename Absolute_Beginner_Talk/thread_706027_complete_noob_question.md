---
title: "complete noob question"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by e6600 on 2008-02-24
"Download the xml files and extract the file into /etc/fonts/ as root:"
i have the xml files, but i cant paste them in etc/fonts/ because idk how to logon as root -_-
how do i do this in terminal?

---

### Post by Crafty Kisses on 2008-02-24
> **e6600 said:**
> "Download the xml files and extract the file into /etc/fonts/ as root:"
i have the xml files, but i cant paste them in etc/fonts/ because idk how to logon as root -_-
how do i do this in terminal?

Are you trying to install fonts? If so, just install kfontview.
```
sudo apt-get install kfontview
```

---

### Post by justin whitaker on 2008-02-24
> **e6600 said:**
> "Download the xml files and extract the file into /etc/fonts/ as root:"
i have the xml files, but i cant paste them in etc/fonts/ because idk how to logon as root -_-
how do i do this in terminal?

Run sudo passwd, and enter your new passward for Root. Then, you can type su, enter that password, and then you can follow those directions.

---

### Post by toa on 2008-02-24
> **e6600 said:**
> "Download the xml files and extract the file into /etc/fonts/ as root:"
i have the xml files, but i cant paste them in etc/fonts/ because idk how to logon as root -_-
how do i do this in terminal?

i recommend to use the graphical mode with 

Sudo nautilus
password-> 


Or you can use krusader which has a root mode which allows file operations easily, if you dont,

sudo apt-get install krusader

---

### Post by Hobo Joe on 2008-02-24
Rather than doing it in the terminal, and easier way to do it would be to open a file browser with root priveleges.

To do this, hit ALT+F2, and type:
```

gksudo nautilus

```

From there, you can paste the files to that location.

---

### Post by e6600 on 2008-02-24
thanks guys!!!

---

