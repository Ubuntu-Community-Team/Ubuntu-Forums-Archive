---
title: "[SOLVED] Creating menu entry in Kubuntu"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2008-04-06
I just installed Neverwinter Nights Diamond and would like to have a menu entry to click and run the game (I'm using Kubuntu 7.10).  Right now I have to go in to a terminal window, cd to the directory and run ./nwn.  I created a menu entry under games and on the command line typed ./nwn.  However, this does not work.  I tried different variations like entering the full path and selecting to Run in Terminal but none worked.  How can I make it work?

---

### Post by luisromangz on 2008-04-06
Try writing nwn in the command, and its path in the "working directory" entry.

---

### Post by notbitmonk on 2008-04-06
Tried it but didn't work.  Variations of the commad that I tried where ./nwn, nwn, nwmain.  Also tried with the option to run in terminal.  I did all this using your suggestion.

---

### Post by luisromangz on 2008-04-06
Then, try creating a shell script that makes the commands you manually perform to play the game (so we now these work), and then call it from the menu icon.

---

### Post by notbitmonk on 2008-04-06
I Know very little about shell scripting.  I created a file with the following but it didn't work.
```
#!/bin/sh
# Run Neverwinter Nights
cd /usr/local/games/nwn
./nwn
```

---

### Post by notbitmonk on 2008-04-07
I forgot to set the permissions of the file to executable.  Now runs fine.

---

