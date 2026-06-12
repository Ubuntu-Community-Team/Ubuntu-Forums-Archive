---
title: "List Directories, NOT Files"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Ek0nomik on 2007-08-22
I am trying to put in a command that will list all subdirectories but ignore files.  I only want directories to be listed, not files.

This is what I did:

```
ls -R Live.Sets >> Live.Sets.txt
```

This outputs all the directories, but *also* the files contained within all the directories.  This is an example of what I want to happen:

I have a directory called Live.Sets, and 2 folders beneath it.  I want my output file to contain the names of both those directories, and any directories beneath those.  Not list any files whatsoever.

I tried using the -d argument, but that didn't do the trick, unless I used it wrong.

Cheers!

---

### Post by funrider on 2007-08-22
```
ls -l | egrep '^d'
```

---

### Post by bodhi.zazen on 2007-08-22
find * <dir> -maxdepth 2 -type d

where <dir> = directory to search. Leave blank = current directory

see man find ;)

---

### Post by Ek0nomik on 2007-08-23
> **funrider said:**
> ```
ls -l | egrep '^d'
```

That doesn't go into subdirectories.

Thanks bodhi, I think that's what I needed.  :)

---

