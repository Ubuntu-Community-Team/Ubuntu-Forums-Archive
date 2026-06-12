---
title: "Getting dpkg to write to a text file ..."
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2006-07-18
I would like to have a look-see at all of the packages and/or applications installed on my ubuntu.  But when I use dpkg -l
it scrolls off the terminal screen and I lose much of it.

Is there a command to write the output to a text file?

I looked through dpkg --help but I am afraid multiple arguments sort of confused me for now.  Thanks!

---

### Post by aysiu on 2006-07-18
Have you tried this? ```
dpkg -l > textfile.txt
```

---

### Post by meng on 2006-07-18
An alternative strategy, if you don't want to output to a file, is to pipe using less, i.e.
```
dpkg -l | less
```
BTW, the strategy of appending "> textfile.txt" or "| less" is not dpkg-specific, and will work with other commands too.

---

### Post by Average_Joe on 2006-07-18
Thanks, aysiu.  That outputs it to a text file but the line-character limit for each line is 126, thus many descriptions get hacked in half by this limitation.  (The descriptions column is the right-most info and that is reason it's getting cut in half or so.)

Is there a way around this, maybe something like dpkg -l > filename.text style:landscape

ok, just kidding -- but is there????   Thanks again

---

### Post by aysiu on 2006-07-18
It doesn't cut off, believe it or not--it just wraps in the text editor.

In Gedit, go to **Edit** > **Preferences** and turn off text wrapping, and you're good.

---

