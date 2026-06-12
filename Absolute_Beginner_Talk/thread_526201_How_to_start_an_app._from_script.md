---
title: "How to start an app. from script?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by tk338 on 2007-08-15
OK, this probably sounds very silly, but I have been a Windows user for years, and only got linux working properly yesterday... I have downloaded Ardour (it said to download the script?), I've downloaded it, extracted the files... now what? How do I get Ardour working?

---

### Post by ThrobbingBrain66 on 2007-08-15
Ardour is already in the repos.  Typing 'sudo apt-get install ardour' in a terminal (Applications > Accessories > Terminal) will install all needed packages for you.  I assume you're running Feisty, so Ardour won't be the lastest version, but you also won't have to worry about compiling source code.

If you insist on compiling the source code, use this site as a reference.
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by tk338 on 2007-08-15
Is there anywhere special I need to put ardour, because it says 'E: Couldn't find package ardour'

---

### Post by ThrobbingBrain66 on 2007-08-15
You may have to enable the universe and multiverse repos.  Go to System > Adminstration > Software Sources

On the first tab, under 'Downloadable from Internet' tick the lines that say universe and multiverse at the end. Then close the window and let it reload your sources.list file.  After that, in the terminal again, type 'sudo apt-get update' and 'sudo apt-get install ardour'

---

### Post by tk338 on 2007-08-15
hmmm they were already ticked, but i tried the update line, and that did lots of things, and the the 'sudo apt-get install ardour' but still cannot find package.

---

### Post by ThrobbingBrain66 on 2007-08-15
Ah ha!  In Feisty, the package is called ardour-gtk. :)
```
sudo apt-get install ardour-gtk
```

The moral of the story is that sometimes it's easier to just search in Synaptic for packages :)
I wouldn't have wasted so much of your time!

---

### Post by tk338 on 2007-08-15
Ah thx, that seems to be doing the trick.

---

