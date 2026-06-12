---
title: "Gnome-terminal log"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by timon_tg on 2007-03-29
Hi,
I would like to ask how to save the output from gnome-terminal in Ubuntu 6.10 to a log file?
10x

---

### Post by tomxyz on 2007-03-29
you have to redirect it from the normal output (the screen) to a file, if I remember correctly you use the " > " sign.

ex:

ls > 'filename'

I read this once in a manual  try typing 'using the commandline' in google linux

---

### Post by timon_tg on 2007-03-29
Not only the output from 1 command . I want to save the output in log file for about 1 h  including the commands , the output , the prompt (everything that can be seen)

---

### Post by Arndt on 2007-03-29
> **timon_tg said:**
> Not only the output from 1 command . I want to save the output in log file for about 1 h  including the commands , the output , the prompt (everything that can be seen)

The terminal emulator 'xterm' used to exist in versions which had an option to turn on logging, but the one here seems not to be one of those.

But you can use the 'script' command.

---

### Post by timon_tg on 2007-03-30
10x script -a -v <logfile> works great for me!

---

