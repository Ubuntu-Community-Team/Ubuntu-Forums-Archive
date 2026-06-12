---
title: "Problem running Shell commands (script)"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by dwhitney67 on 2007-06-14
Hi,

I am trying to figure out why on Ubuntu the /bin/sh (or dash) does not "like" the following statement:

[FONT="Courier New"]mkdir -p foo/{dir1,dir2}[/FONT]

The statement executes, but the result are wrong.  Instead of creating two subdirectories below the directory "foo", mkdir creates a directory with the name of "{dir1,dir2}".

I am running Ubuntu 7.04 (Feisty) and it appears that the /bin/sh is a link to /bin/dash.  What is dash?  Is it a bash wannabe?  On my system /bin/sh is now setup to point to /bin/bash.

---

### Post by mcduck on 2007-06-14
> **dwhitney67 said:**
> Hi,

I am trying to figure out why on Ubuntu the /bin/sh (or dash) does not "like" the following statement:

[FONT="Courier New"]mkdir -p foo/{dir1,dir2}[/FONT]

The statement executes, but the result are wrong.  Instead of creating two subdirectories below the directory "foo", mkdir creates a directory with the name of "{dir1,dir2}".

I am running Ubuntu 7.04 (Feisty) and it appears that the /bin/sh is a link to /bin/dash.  What is dash?  Is it a bash wannabe?  On my system /bin/sh is now setup to point to /bin/bash.

Dash is much lighter and faster shell than Dash is, and that's why /bin/sh is now pointing to it instead of much heavier Bash.

If your scripts need Bash, you should tell it in the first line of the script (like you should be doing anyway). JUst put the following string on the first line and everything works fine:
```
#!/bin/bash
```
This will tell Linux to run the script using Bash as shell. I recommend keeping the /bin/sh pointing to Dash as Dash can handle your system tasks much quicker than Bash does..

[https://wiki.ubuntu.com/DashAsBinSh]("https://wiki.ubuntu.com/DashAsBinSh")

---

### Post by dwhitney67 on 2007-06-15
Thanks for the reply.  It was not a script that I was running.  It was a Makefile.  For instance, something like:

[FONT="Courier New"]$ make all[/FONT]

where the Makefile looks something like:

[FONT="Courier New"]all:
[INDENT]mkdir -p foo/{dir1,dir2}[/INDENT][/FONT]

Is there a place where one can specify which shell to run when executing shell script within a Makefile?

---

### Post by big_gie on 2007-07-30
Use :
```

SHELL := /bin/bash
[...]

```
in your makefile.

[http://www.gnu.org/software/make/manual/make.html#Choosing-the-Shell](http://www.gnu.org/software/make/manual/make.html#Choosing-the-Shell)

---

