---
title: "Can't Edit sources.list from Command Line [Resolved]"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Kerry Lange on 2007-02-03
I'm trying to overcome some problems with using a new nVidia 8800 card, along with a new motherboard.  The X server won't run.

So, I'm trying to get at the latest nVidia drivers using the command line.  I've installed Feisty because it will run with my new (Intel 965p-based chipset) motherboard, while Edgy won't.

When I press "ctrl + alt + F1" to go to the command line, then go to edit the sources.list file, instead of opening the file, I get the following:

2078


"2078 and a blank line" with the cursor blinking back at me.  I can open another terminal and do the same thing but the same thing happens.

I'm using the "ed" command to edit the file.  Am I doing something wrong or is something failing on me?

---

### Post by lamego on 2007-02-03
Open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by HadroLepton on 2007-02-03
ed is some sort of special purpose text editor, the man page says "line-oriented text editor", whatever that means.

use nano or vi to edit text files.

---

### Post by Kerry Lange on 2007-02-03
> **lamego said:**
> Open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```

That doesn't work either.  I tried that first but I got an error message.  I gather that the "g" before "edit" stands for "graphical."  I thought I got the error message because the "gedit" command isn't available from the command line.

> use nano or vi to edit text files.

Okay, I'll give that a try.

---

### Post by Kerry Lange on 2007-02-03
Well, nano worked.  Thanks!

---

### Post by 23meg on 2007-02-03
> **lamego said:**
> Open a terminal and type:
```
sudo gedit /etc/apt/sources.list
```
Just for the record, for graphical apps such as gedit, you should use *gksudo* instead of *sudo*.

---

