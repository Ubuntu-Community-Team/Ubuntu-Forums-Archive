---
title: "mutli-program quick launch?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by insub2 on 2007-07-31
I was wondering how to make one quick launch button launch multiple programs.  specifically, all my browsers for when i'm building webpages.

thanks in advance.

---

### Post by Pragmatist on 2007-07-31
> **insub2 said:**
> I was wondering how to make one quick launch button launch multiple programs.  specifically, all my browsers for when i'm building webpages.

thanks in advance.

You use a script.  Open and editor and type this (replacing with your browsers):

```

**#!/bin/sh**

#Script for launching multiple programs with one click

mozilla **&**
epiphany **&**
firefox **&**

```

Notice that all you need is to put **#!/bin/sh**  as your first line, then you put each program on a seperate line ended with an **&**  The **& **insures the program is run in the background and allows the next program to run without waiting for the first to finish.  

Save the file and make is executable (I'll pretend you saved it as "testscript"):
```
chmod a+x testscript
```

Now just Right-Click on the panel, choose "custom launcher" and under "command" put this:
```
/bin/bash testscript
```

That's it!

---

### Post by Rocket2DMn on 2007-07-31
If you are making a launcher, when you tell it what command to run, you should be able to give it multiple:
command: mozilla && epiphany && firefox &
or some such thing.  I'm not in front of my box to test that, but it should work.

---

### Post by insub2 on 2007-07-31
Thanks Pragmatist!

Rocket2DMn, your method didn't seem to work for me.

---

