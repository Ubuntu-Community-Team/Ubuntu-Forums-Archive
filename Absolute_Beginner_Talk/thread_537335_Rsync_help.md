---
title: "Rsync help"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by ace214 on 2007-08-28
I've tried several things to get rsync to copy all my flac files from my music directory to a new directory to convert them and I can't figure it out.

I've tried this : rsync --include-from rules -r /media/MMMM/Music ~/Music
with the include file saying
+ */
+ *flac
- *

but it simply copies everything. I don't know why it's not excluding everything that doesn't match the first two rules....

Any help would be appreciated.

Note: the reason I am doing this is because I can't get pacpl to isolate flac files on it's own, so if anyone knows how to do that, it would be great. The help file doesn't help so I'm thinking about contacting the author....

---

### Post by p_quarles on 2007-08-28
The rsync utility is kind of overkill for what you're attempting to do. Try this instead:
```
cd ~/Music
sudo cp -r *.flac /media/destination/directory
```
Unless I'm missing something (please tell me if I am), that should do the trick.

---

### Post by ace214 on 2007-08-28
ok thanks.

---

### Post by ace214 on 2007-08-28
Errr, ok:
```
me:/media/MMMM/Music$ sudo cp -r *.ogg ~/Music
me:/media/MMMM/Music$ sudo cp -r *.flac ~/Music
cp: cannot stat `*.flac': No such file or directory

```
So the first time it gives no error and doesn't copy anything. The second time it gives that error.

---

### Post by ace214 on 2007-09-02
Still looking for help on this.... Again, need to copy all of a certain type of file (oggs) to another directory preserving the tree. cp just won't recurse unless I copy the whole directory....

---

### Post by ace214 on 2007-09-03
Last bump....

---

