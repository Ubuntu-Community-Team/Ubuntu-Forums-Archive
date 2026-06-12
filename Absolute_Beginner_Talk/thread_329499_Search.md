---
title: "Search"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-01
Is there a trick to file browser search or a more detailed guide.

I am wanting to look for files on the hard drive but It appears I can only search files in the current directory and not the whole drive.

Do I need to install a different file browser or is this one of unix limitations.

---

### Post by meng on 2007-01-01
Assuming you are going to Places > Search, the field for "Look in Folder..." is a drop-down menu, you can choose filesystem which will search EVERYTHING, or you can choose a custom folder to search (recursively).

---

### Post by testube_babies on 2007-01-01
One of the things I hate about Gnome is the search limitations.  Supposedly, Gnome is fully searchable, but I always get better results doing it from the command line:

```
sudo updatedb
locate search_pattern
```

where search_pattern is whatever you're searching for.

---

### Post by rbhigday on 2007-01-01
> **meng said:**
> Assuming you are going to Places > Search, the field for "Look in Folder..." is a drop-down menu, you can choose filesystem which will search EVERYTHING, or you can choose a custom folder to search (recursively).

Nope I was in places > computer and using the search function in there. it not as good as the one you pointed out. :) I feel like a moron for not noticing the listing. :)

Thanks

---

### Post by wilberfan on 2007-01-08
I've been using Ubuntu for a few months now, and I'm just noticing that Search doesn't look everywhere -- or at least doesn't seem to find things everywhere.   Even if I specify "File System", it doesn't seem to be looking in all my partitions...   To test this I created a text file on /media/sdb5 and no amount of searching seems to find it!   Even 'locate' couldn't find it..

Am I doing something wrong?   Are there other search options?   Other search software??

---

