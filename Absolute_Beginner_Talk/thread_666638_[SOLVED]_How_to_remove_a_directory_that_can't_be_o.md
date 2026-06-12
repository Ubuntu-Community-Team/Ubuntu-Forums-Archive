---
title: "[SOLVED] How to remove a directory that can't be opened?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by SherpaDoug on 2008-01-13
I untarred something to my desktop and it made a directory I can't seem to remove.  It is called "doc" and I believe it contains HTML on how to use iperf, but I just want it gone.  I don't have "permissions" to even open it.  Its owner is '504'.  I have tried "sudo rmdir doc" and "sudo rm doc -d" to no avail.

---

### Post by Dr Small on 2008-01-13
Try logging into Nautilus as root:
```
gksudo nautilus
```

And browsing to /home/USER/Desktop and see if you can delete it that way.

Dr Small

---

### Post by dhughes on 2008-01-13
What about 

 ```
 sudo rm -R ~/Desktop doc 
```

---

### Post by SOULRiDER on 2008-01-13
> **dhughes said:**
> What about 
 ```
 sudo rm -R ~/Desktop doc 
```

That should be
 ```
 sudo rm -R ~/Desktop/doc 
```

---

### Post by SherpaDoug on 2008-01-13
Cool! It worked!
What is "gksudo" and what is "nautilus"?  Is it another GUI that doesn't use permissions the same way?

---

### Post by SOULRiDER on 2008-01-13
Nautilus is your file browser.
gksu will run an application as root, much like sudo does. Wheny ou did gksu nautilus you ran the file browser as root so you could remove the directory.

---

### Post by SherpaDoug on 2008-01-13
Thanks, the dim outlines of understandable architecture are starting to emerge from the fog that is a new OS.  In time I will understand.  Without this community I would be lost.

---

### Post by SOULRiDER on 2008-01-13
Dont worry, we were all newbies once (and most of still are :P). With time youll come to understan better how things work, things will seem a lot less confusing soon, dont worry about it.

Just post when you have questions.

Alos, could you please mark the thread as solved? Its really simple, just check out these steps. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

