---
title: "Recursive Move Question"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Kaobear on 2008-01-27
I know this has a simple answer, I am afraid I just can find it.

I have about 50 directories on my desktop.

Each folder, of course, contains such and such amount of files.

What is the command, for I am sure there is one, to move all the files in those directories, and not the directories themselves to another directory, thusly saving me hours of copy and paste and all of that nonsense?

Any help is appreciated I assure you.

---

### Post by blueridgedog on 2008-01-27
```
mv ~/Desktop/myfolder/* /path/to/new/folder
```

---

### Post by tribaal on 2008-01-27
Using "find" you can achieve something like this:

```
find <root of your subdirectories> -type f -exec mv {} <target directory> \; 
```

(The -type f switch specifies "any regular file" (non directory or link etc...)

Hope this helps!

- Trib'

---

### Post by Kaobear on 2008-01-27
> **tribaal said:**
> Using "find" you can achieve something like this:

```
find <root of your subdirectories> -type f -exec mv {} <target directory> \; 
```(The -type f switch specifies "any regular file" (non directory or link etc...)

Hope this helps!

- Trib'

Exactly what i was looking for, thanks a million.:KS

---

### Post by ~LoKe on 2008-01-27
Wouldn't this theoretically work, as well?  Seems much simpler..
```
## ~/bigfolder contains all 50 directories
mv ~/bigfolder/*/* ~/newfolder/
```

---

### Post by tribaal on 2008-01-30
Yeah it would work, but only for a fixed-depth search, and only for files in the lowest-depth dierctory...

- Trib'

---

### Post by blueridgedog on 2008-01-30
I think it is time to at a -R switch to the mv command.  

I seen this accomplished with complex pipes to tar and back and other ways, but it seems odd that we lack a recursive feature.

---

