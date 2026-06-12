---
title: "[SOLVED] How do I make bash scripts?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-01-25
I'm trying to make 2 simple scripts, but I lack the basic fundamental knowledge of how scripts are made. :p
I want one to run the commands:

xrandr --output VGA --mode 1280x1024
xrandr --output LVDS --off

and another to run:

xrandr --output LVDS --mode 1280x800
xrandr --output VGA --off

Then I want to assign these scripts to hot keys with xbindkeys.
I'm not 100% on how to tell xbindkeys-config what key combos I'm trying to assign commands too. I've been reading the xbindkeys manual, and I don't seem to understand very well, because I can't get the -mk command to work so I can figure out what to type into xbindkeys-config key area...

---

### Post by Brunellus on 2008-01-25
bash scripting in general: 

Write your script in the Text Editor of Your Choice.  (I prefer vim).  The first line will be 

#!/bin/sh

Then type your other commands.  

When you're done, save.  then you'd need to make the script executable with 

chmod +x SCRIPTNAME.

you'd execute it with

./SCRIPTNAME

---

### Post by Jeezus on 2008-01-25
Thanks Brunellus!
I really appreciate that. It's much easier than I thought.
So in order to associate this script with a shortcut key, I would have to type in path to the script, right? so it would be:
path/to/script/SCRIPTNAME
right?

---

### Post by Brunellus on 2008-01-25
yup, you'd use the full path to the script.  I'd execute it with 

sh /path/to/SCRIPT.sh

in that case.

---

