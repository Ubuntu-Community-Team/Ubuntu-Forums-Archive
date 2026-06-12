---
title: "File search app?"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-04-27
Is there a better application to search for files under Ubuntu? I dis-like the default one. (I imagine its the default one for Xfce, not sure if its the same on Gnome or KDE.)

---

### Post by hw-tph on 2006-04-27
Learn the **find** command. It is incredibly powerful. Read the man page, at the bottom there are several examples. Also **locate** can come in handy.


Håkan

---

### Post by frodon on 2006-04-27
The locate command is really nice too.
First run a : ```
sudo updatedb
```It creates a database of all the path of your computer
Then to search a file : ```
locate file_name
```It works even if you put only the first characters of the filename
To search gif file for example : ```
locate *.gif
```
However you have to update the database sometimes as to be up to date, a cronjob do that really well.

---

### Post by patrick295767 on 2006-04-27
krusader works for it too ..

---

### Post by mostwanted on 2006-04-27
You can install Beagle + deskbar. It's similar to Spotlight in OSX or Google/MSN desktop search.

---

