---
title: "deleting files in sub folders"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by dragobr on 2007-05-09
Hello all! Is there a way to delete all files that begins with "Al" on a folder and sub folders?

rm --recursive Al* only looks for file on the current directory.. =/

---

### Post by Martin on 2007-05-09
I'd test this without the rm bit first - but this should work
rm `find /home/whatever/*/*filename.txt` 
This will use the the find command to... well find the files you want to delete. Once found the rm command will delete them. The quote marks to be used are the ones underneath the esc key. The first * is to denote any and all dirs under /home/whatever/

---

### Post by jonlink on 2007-06-27
Looks like that would only work on files that have no spaces, otherwise things go pretty badly.  Any idea how to work around that?

---

### Post by jonlink on 2007-06-27
Wait, I know this one!  The find command with the -delete thingy will do it I think.  Something like this should work (be careful, there is no way to undo the delete!)
```
 find . -name *.log -delete;
```
This is another one where you can get rid of "-delete" to see what it is you'll delete.  It work from the directory you are currently in and deletes whatever it find finds. In my case it is a bunch of annoying log files

---

### Post by mig5 on 2007-06-27
> **jonlink said:**
> Looks like that would only work on files that have no spaces, otherwise things go pretty badly.  Any idea how to work around that?

You need to put a backslash '\' before each space.

Example:
```
rm /hda1/Program\ Files/Internet\ Explorer
```

---

