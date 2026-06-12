---
title: "Problem with find, possible bug"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by CareySchug on 2006-11-28
Why do these commands work (in that they find what you would expect them to find)

find . -name mcca*.*
find . -name MCCA
find . -name "MCCA*.*"
find . -name .MCCA*.*
find . -name FMCCA*.*
find . -name MMM*.*
find . -name MCA*.*
find . -name MCAA*.*
find . -name MCCAA*.*
find . -name MCCA?
find . -name MCCAAx*.*
find . -name MCCAx*.*

but entering any of:

find . -name MCCA*.*
find . -name MCCA*
find /home/user -name MCCA*.*
find . -name MCCA?*
find . -name MCCApp*.*

give the error message

find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]

Note: the files I was originally looking for were of the form MCCApp*.*, but even when the last two successfull searches above worked even when I created files files MCCAAxx.pdf and MCCAxx.pdf (so they found something) the command did not fail.

OK, I know why, but I don't know if it is a BUG or some design limitation I don't know of.  This is in Ubuntu 6.06, with current (as of yesterday) patches.

The failure is when a file would be found that is a "long" filename.  I created (touched) a file MCCAAxxverylongnamejusttotest.pdf and the find for it gave the error message.

---

### Post by CareySchug on 2006-11-28
OK, if I go up a level in the directory, no error message. It's caused by the shell expanding the name, and the only time there was more than one hit (so the expansion produced a list instead of a single entry) was when the names were long.

So, my apologies, cancel this thread.  I'm just glad I figured it out before I hit enter on the bug report I started.

aside: is find a built-in in unix, or at least the korn shell, which doesn't expand anything after the "-name"?  I don't remember having to use quotes in unix, but maybe I was just lucky and never had any matches in the current directory.

---

