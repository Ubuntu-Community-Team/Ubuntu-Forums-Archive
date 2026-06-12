---
title: "[SOLVED] How to add random quotes to terminal?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by orange2k on 2007-09-13
Ive seen it in Mint: whenever you open the console, some random quote appears.
How can I add something like that to my Ubuntu console?:)

---

### Post by Nulifier on 2007-09-13
This is actually quite neat and I implemented it while writing this

So what you do is make sure you have fortunes installed
type: *fortune*
in the console if it works then you are finished and you can go on if you need to install it install the package with *sudo apt-get install fortunes*

after this is done type:

gksudo gedit ~/.bashrc
and add this onto the end of the file and save

```
if [ -x /usr/games/fortune ]; then
     /usr/games/fortune -s
fi
```

then this should be done (tested on gutsy with gnome)
if you wish to get longer quotes you can remove the -s on the command in .bashrc
and you can also fool around with any of the options
have fun!!!

---

### Post by orange2k on 2007-09-13
I like...
Hehe, its like someone said: kitty has reached critical mass...

---

