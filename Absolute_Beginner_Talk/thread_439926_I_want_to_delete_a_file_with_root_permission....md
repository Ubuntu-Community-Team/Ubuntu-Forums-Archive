---
title: "I want to delete a file with root permission..."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by volksolwagen57 on 2007-05-11
I'm trying to delete a directory with files in it i tried this:
> sudo rmdir (directory)
i found that i needed to changer permission, so i did this:
> sudo chown -R (directory)
this didn't work what did I miss? i want to delete a directory with a bunch of files in it. it was a bad install and i don't want to deal with it anymore. someone help!?

---

### Post by Najand on 2007-05-11
You cannot use rmdir when that directory is not empty.
Try:```

sudo rm -rf (direcotry)

```

---

### Post by MoxJet on 2007-05-11
You can basically use rm to remove your whole harddrive ( sudo rm -rf / ), so it might be a good idea to have the -i switch on to confirm every delete.
```
sudo rm -rfi /path/to/delete
```

---

### Post by Najand on 2007-05-11
In fact that is true. Thanks Moxjet.

---

### Post by ajgreeny on 2007-05-11
Just be careful you don't remove something important.  System files are usually important so make sure you know exactly what they are before you get rid of them and then regret it.  Wise to back up anything you remove in terminal first as there is no backup in trash or anywhere else if you use terminal.

---

### Post by hartz on 2007-05-11
Many a systems admin have made a typing mistake like this

```
sudo rm -r / usr/home/joe
```

Note the offending space after the first slash...

---

