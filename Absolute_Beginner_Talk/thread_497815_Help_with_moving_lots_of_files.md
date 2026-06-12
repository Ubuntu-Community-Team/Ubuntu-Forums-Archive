---
title: "Help with moving lots of files"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Nadstar on 2007-07-10
Hi All,

I have recovered data from a friends hard drive that had Win XP installed and that had become unbootable and unrepairable. I used a program called photorec (part of testdisk) - its a good app :)

Now I have 54 directories with 500 files in each. I need to be able to move these files into a single directory for sorting/deletion. Is there an 'mv' command that I can use to do this, without going into each directory in-turn?

---

### Post by benerivo on 2007-07-10
I don't know of any directory move command, but i've done something similar in windows before. By searching the parent folder of these 54, for all files (ie. do a blank search to return all files), you can then use the search results window to select all, and then copy or move to a single new folder - this may take some time if there are several gigs of data.

---

### Post by Ek0nomik on 2007-07-10
I could be mistaken, but I believe something like this would work:

```
mv *name.of.directory.with.all.my.files*/* *name.of.directory.where.I.want.my.files*
```

The * acts as a wildcard to look at all files in the directory, not just a specific one.  You could make a folder with two files and try to move them somewhere else to test it.  I am at work on Windows XP, so I can't check for you.  :(

---

### Post by punx45 on 2007-07-10
> **Ek0nomik said:**
> I could be mistaken, but I believe something like this would work:

```
mv *name.of.directory.with.all.my.files*/* *name.of.directory.where.I.want.my.files*
```

The * acts as a wildcard to look at all files in the directory, not just a specific one.  You could make a folder with two files and try to move them somewhere else to test it.  I am at work on Windows XP, so I can't check for you.  :(


as you have it , that would not act recursively.   If acting recursively, it would replicate the directory tree.   i think OP is looking to assemble all files en masse in one directory.



im thinking...

this seems to do the trick:   see if it makes sense to you:
[http://www.pelennorfields.com/matt/2004/10/03/581/](http://www.pelennorfields.com/matt/2004/10/03/581/)

---

### Post by Nadstar on 2007-07-11
Cool - will give the scripting a go. Cheers.

---

