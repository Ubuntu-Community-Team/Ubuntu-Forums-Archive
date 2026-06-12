---
title: "[SOLVED] Print From Terminal"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-09-13
I have an HP Photosmart C5180 All-in-One printer. It works perfect. Now, I want to find a way to print from the terminal. Is there some location that I can redirect the output of a command to? Or is there a certain print command I can use? There has to be some way to do this. Any help would be appreciated.

---

### Post by agds on 2007-09-13
I'm pretty sure Ubuntu has LPR and/or CUPS preinstalled.  I'm unfamiliar with the usage, so I won't be able to give you specifics.  Try ```
sudo apt-get install lpr
man lpr
``` and see if that gets you anything useful.  Alternately, you could redirect the output to a file, e.g. ```
tail /var/log/Xorg.0.log > filename
``` and open it in an editor like Vim, which has a :hardcopy command.  You should probably do ```
:set printoptions=paper:letter
``` to set the paper size (from within Vim) if you're going to print from there.

---

### Post by nhandler on 2007-09-14
Well, lpr did the trick.
With lpr, you can pass it the path to a file to print.
So for example, I could do
```
lpr ~/printme.txt
```
If you don't pass it the path to a file, it reads from the standard input. This allows you to pipe the output of a command to lpr.

---

