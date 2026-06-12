---
title: "How to run a Python script?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-05-13
Hi,

I'm using Kubuntu Feisty.

I'm trying to run  the Python script at [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/).

Here's the part where I get stuck...

> Third, put rebuild_db.py into the iPod's root directory and start it. A double-click should do; if not, you have to open a terminal yourself and chdir to the iPod's root directory (i.e. the drive letter on Windows or /Volumes/NameOfYourIPod on Mac OS X) and start the script manually with `python rebuild_db.py'. The program will scan the iPod volume for playable files. It also creates file called rebuild_db.log.txt that contains the program's output messages. If you don't find error messages there, everything should be OK.

When I double-click on the rebuild_db.py file, Kate opens it.

Could someone please tell me how to either change what happens when I double-click the file so the right thing happens, or what command to enter into Konsole to get the script to run?

Thanks heaps.
Trisha

PS. I've searched the forums and Google with no luck.

---

### Post by bodhi.zazen on 2007-05-13
Open a terminal

cd into the directory that contains "rebuild_db.py"

Then enter ```
python rebuild_db.py
```

---

### Post by szymon_g on 2007-05-13
or try:

sudo chmod +x script.py

./script.py

---

### Post by trishacupra on 2007-05-13
> **bodhi.zazen said:**
> Open a terminal

cd into the directory that contains "rebuild_db.py"

Then enter ```
python rebuild_db.py
```

Thanks. I'm a real beginner. How do I *cd into a directory*? :confused:

---

### Post by Dr Small on 2007-05-13
open the terminal and type
```

cd director
```

If the address to the directory has spaces in it, type:
```

cd "directory/with a space"

```

Hope that helps. ;)

Dr Small

---

### Post by trishacupra on 2007-05-13
Thanks! I'll give it a bash.

---

### Post by trishacupra on 2007-05-13
It worked! Yay! Thanks guys.

---

