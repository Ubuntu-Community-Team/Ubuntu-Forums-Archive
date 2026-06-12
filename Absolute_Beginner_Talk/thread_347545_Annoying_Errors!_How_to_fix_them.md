---
title: "Annoying Errors! How to fix them?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tenkabuto on 2007-01-27
Okay, I keep getting this same [error](http://i19.photobucket.com/albums/b160/tenkabuto/error.png) when trying to add a program and [this](http://i19.photobucket.com/albums/b160/tenkabuto/meh.png) when I try to update.

These are the only errors I know of for now, someone please help me.

---

### Post by JamieC on 2007-01-27
Open a new terminal window (Applications -> Accessories -> Terminal) and type the following:
```

sudo apt-get install -f

```

What is the output?

---

### Post by dwblas on 2007-01-27
You will have to also post what happened after you did what the 2nd message said as a fix.  It appears your local repository is corrupt and has to be rebuilt.  One of the reasons for this is a bad spot on disk, or bad memory (unless you did something yourself), so you definitely want to backup your system regularly.

---

### Post by tenkabuto on 2007-01-27
> **JamieC said:**
> Open a new terminal window (Applications -> Accessories -> Terminal) and type the following:
```

sudo apt-get install -f

```

What is the output?
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

---

### Post by geekgod on 2007-01-27
sudo dpkg --configure -a

---

