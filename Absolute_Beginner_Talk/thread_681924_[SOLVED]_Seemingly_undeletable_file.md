---
title: "[SOLVED] Seemingly undeletable file"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Rodney2 on 2008-01-29
When I am in the terminal and type ls -ls to get a lesting of the contents of the directory, I find a file that I had somehow created when experimenting with gimp that reads
4 -rw-r--r-- 1 rodney rodney    1 2007-07-24 13:00 This is a test saving a file in gimp
I can not seem to find a way to delete this file.  Any other file created i can remove with the rm command but I can't seem to access this one with all the spaces in the title.  Any solution?  Thanks  Rodney

---

### Post by TBerben on 2008-01-29
You need to escape the spaces in the file name: put a backslash in front of it. Or use bash's tab-completion: begin typing the filename and hit tab to have bash complete it for you.

---

### Post by emarkd on 2008-01-29
Two things to try:  Try wrapping the filename in quotes:

```
rm "This is a test..."
```

or escaping all of the spaces

```
rm This\ is\ a\ test...
```

---

### Post by y-lee on 2008-01-29
Try putting quotes around the file name when ya use rm. If ya don't have permission then sudo rm

---

### Post by Rodney2 on 2008-01-29
Thanks a bunch, by putting the backslash in front of each of the spaces did the job.  Thanks, thanks thanks   Rodney

---

### Post by bodhi.zazen on 2008-01-29
LOL or use tab completion :

rm This<tab>

---

