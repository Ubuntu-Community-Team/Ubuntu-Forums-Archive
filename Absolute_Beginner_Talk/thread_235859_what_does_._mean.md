---
title: "what does ./ mean?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-08-13
for some reason to run cairo-dock i must first go to its directory and then instead of just typing cairo-dock (the name of the executable) i have to type ./cairo-dock.
my question is why?

also i would like to make cairo-dock run when the sytstem starts. what do i need to type into my sessions thingy to make cairo-dock run on start up?

Thanks!

---

### Post by BitTorrentBuddha on 2006-08-13
It's equivalent to path to current directory. Running apps requires you to provide the file path (unless it's in a bin directory.)

---

### Post by 23meg on 2006-08-13
The dot represents the current directory. 

*./foo* means to the shell "the executable *foo *which is in my current working directory". *foo *alone would have meant "the executable *foo *which is in my default path".

---

### Post by NitsBITS on 2006-08-13
If you come from a microsoft background, like I do, the dos/xp command line interpreter(shell) implicitly checks for the existence of the executable in the current directory as well as in all directories listed in the path (if needed). 

Bash, and probably other *nix shells, don't implicitly add the cwd(current working directory) to your environment. So, when executing something living in a directory which is **not **in your path, you must *explicitly* _give bash both the path AND the name of the file to run._

As 23meg mentioned, ./filename_to_run will do this for you. Breaking this down, . (dot) refers to the current directory, / (forward slash) as the separator, and finally the file to run.

Hopefully, this makes sense.:) 

alex

---

