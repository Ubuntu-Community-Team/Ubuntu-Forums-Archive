---
title: "Find file?"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by ubuntunooob on 2005-12-27
How do you search the file system for a particular file?

---

### Post by Kindred on 2005-12-27
Places > Search for Files...

---

### Post by bscbrit on 2005-12-27
Using the command 'find'. For example

find / -name '*.txt'

will find everyfile, starting at the top '/' directory that matches the name specification given.

find ~ -size +20k

finds all the files in your home directory and subdirectories that are larger than 20kb.

See 'man find' for loads of other options

---

### Post by Rinzwind on 2005-12-27
or from CLI

```
sudo find / -name {filenamewith(ifneeded)wildcards} -print
```

Grrrr @ bscbrit

---

### Post by ubuntunooob on 2005-12-27
[QUOTE=Kindred]Places > Search for Files...[/QUOTE]

Thanks!

---

### Post by GoldBuggie on 2005-12-27
I just have to add one more way;)
```

locate <search-phrase>
```

this one is faster but won't get super new files since they aren't in the database which it uses.

---

### Post by ubuntumaneh on 2005-12-27
You can update the database before using the locate (it is done everytime you boot, though):

sudo updatedb

It take a while.

---

### Post by Gowator on 2005-12-27
Anyone know how to tget the KDE search from konqueror working (not the one which uses locate)

---

### Post by Gowator on 2006-01-03
anyone?

---

### Post by estel on 2006-01-03
Are you refering to KAT?

---

### Post by Gowator on 2006-01-03
[QUOTE=estel]Are you refering to KAT?[/QUOTE]
Not sure it used to be in the tools menu then after some upgrades got replqced with the present locate based one ....

---

### Post by Gowator on 2006-01-04
In fact checked out KAT and nope its really just a front end to find I am looking for...
it was useful because it can do files modified between x and y etc. but all I want is basic last atime etc.

---

