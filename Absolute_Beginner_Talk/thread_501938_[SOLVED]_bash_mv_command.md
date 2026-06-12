---
title: "[SOLVED] bash mv command"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by fontenot_1031 on 2007-07-15
Following a setup for Nexiuz on GtkRadiant I'm having trouble moving the "nexiuz.game" file to /opt/gtkradiant/games directory.
I've been using this command.
```
sudo mv /home/devdavad/nexiuz.game /opt/gtkradiant/games
```
and I get this
```
mv: cannot stat `/home/devdavad/nexiuz.game': No such file or directory
```

Any help is much appreciated because I'm just a stupid newb OKAY??!  Jeez

---

### Post by fontenot_1031 on 2007-07-15
...bad title description

---

### Post by roncrump on 2007-07-16
> **fontenot_1031 said:**
> 
```
mv: cannot stat `/home/devdavad/nexiuz.game': No such file or directory
```


What is the output of
```

ls -l /home/devdavad

```

The error message implies that the file is not in the directory from which you are trying to move it. Or the directory itself is missing.

The ls command, with the -l option will list all the contents of the /home/devdavad directory with size, modification date and ownership information. Might be illuminating.

Ron.

---

### Post by fontenot_1031 on 2007-07-16
yeah, it didn't work.  RRR, so aggravating.

---

### Post by jusmurph on 2007-07-16
did you copy&paste Ron's suggest command?

That character that looks like a number "1" is actually the letter "l"

---

### Post by fontenot_1031 on 2007-07-16
yes of course.  Very funny

---

### Post by freebird54 on 2007-07-16
If that is the file's location, it would work.  It would be an unusual directory for it to arrive in though... maybe /home*/username* is more likely? Or even simpler - cd to the location of the file and just
```

 mv nexiuz.game /opt/gtkradiant/games
```

Either should work fine.  Why the sudo though?  Is it a root-owned file?

---

### Post by fontenot_1031 on 2007-07-16
ok sudo nautilus worked

---

