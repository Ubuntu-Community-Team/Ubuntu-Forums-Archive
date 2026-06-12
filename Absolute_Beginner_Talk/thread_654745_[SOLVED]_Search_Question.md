---
title: "[SOLVED] Search Question"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Ancient One on 2007-12-31
Is there a way to search the entire drive including the hidden files and folders? Trying to find something that starts with . is nearly impossible

---

### Post by jan quark on 2007-12-31
try the command
```
locate bla bla
```
type it into the terminal.

---

### Post by taurus on 2007-12-31
```
sudo find / -name **filename** -print
```

---

### Post by NilsE on 2007-12-31
The "Search for files" tool under places works pretty good but you do have to tell it to look for hidden files.

In the Select more options pull down select "Show hidden and backup files"  then each time you open the search tool click on the select more options twistie and it will be there.  You do have to click on the select more options each time so it knows you want to use the options you set.

---

### Post by capink on 2007-12-31
```
sudo find / -iname '.*'
```

---

