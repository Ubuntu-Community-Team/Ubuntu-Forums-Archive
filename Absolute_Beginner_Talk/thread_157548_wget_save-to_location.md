---
title: "wget save-to location"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-04-09
How do I tell wget to save to a specific location?

---

### Post by cwaldbieser on 2006-04-09
[QUOTE=tux101]How do I tell wget to save to a specific location?[/QUOTE]
The -O option lets you save to a specifc file.  If you want to get more than one page, it concatenates them, though.  If you want to save a hierarchy of pages to a specific directory, I would suggest a wrapper script that just cds to the folder you want before running wget.

---

### Post by tux101 on 2006-04-09
What are you answering to?  I said "location".  In other words, directory.  How do I specificy where I would like to download to when I use wget?  It keeps on saving to the current directory, and I don't feel like changing directories.

---

### Post by jeremdow on 2008-03-02
Old thread - but in case anyone's googling - pretty simple - wget just saves to the location from which you run the command.

So when you launch a terminal and start from your home folder - anything you download will be saved there - but all you have to do is change directories - cd - to where you want to store the files, and then wget them from there.

---

### Post by louman on 2008-04-08
I'm not horribly familiar with wget, but if it's true that you cannot specify the path to where you want to download your file(s), the simple solution would be to wrap the command up in a pushd/popd block, like so:
```
$ pushd <desired path>
$ wget <...>
$ popd
```

pushd is like cd, except it remembers the last directory you were in, and popd simply returns to the last directory from which pushd was called. (It does keep track of multiple directory changes on it's own stack. :) )

This isn't as nice as just passing a path to wget, but it's simpler than using cd for multiple paths.

---

