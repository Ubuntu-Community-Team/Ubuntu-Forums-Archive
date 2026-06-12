---
title: "Environmental variables with script"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by wkleu on 2007-11-09
Hi

I want to write a small script I can run to set specific environmental variables. This is my script at the moment:

[I]#!/bin/sh
export JAVA_OPTS="$JAVA_OPTS -Doption.id=something -Doption.else=TEST -Dfile.encoding=ISO-8859-1"
[/I]

It doesn't want to work if I run it from the console (I have set executable rights). It just does nothing. I have tried doing it with sudo but doesn't work either.

When I just copy and paste the command directly into the console it works 100% but it doesn't when I am trying to run it as a script.

This is something I want to manually set and not run every time I log on.

Any help/ideas will be appreciated.

---

### Post by jordanmthomas on 2007-11-09
The problem is that when you make the script an executable file, a new instance of /bin/sh is called.  This instance of sh has the variable set, and then closes.  This leaves the shell you're using untainted (a good thing, really).

Here's one way you could do what you're wanting.
```
nano ~/.bashrc
```
Put this in there
```
alias something='JAVA_OPTS="$JAVA_OPTS -Doption.id=something -Doption.else=TEST -Dfile.encoding=ISO-8859-1'
```
and start up a new shell.
Now, when you type 
```
something
```
JAVA_OPTS will be set.

There are likely other solutions as well, but this is the first one that popped in my head.

**edit**
by the way, if you still don't understand why what you're doing doesn't work, let me know and I can try to explain a little better.

---

### Post by wkleu on 2007-11-09
Thank you very much. It works perfectly.

I wasn't aware that running a script runs a new instance of the shell (but it does make sense).

---

### Post by fatmano on 2007-11-09
try to source the command e.g.
. mySmallScript.sh

notice the . ( dot ) infront of the command.  This places it into your running shell.  This is also how you would add something to your .bashrc file and get it w/o logging out and logging back in.

HTH

-eo

---

