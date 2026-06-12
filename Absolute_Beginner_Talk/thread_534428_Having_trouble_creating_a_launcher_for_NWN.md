---
title: "Having trouble creating a launcher for NWN"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by escape_goat on 2007-08-25
Hi all,

I installed Neverwinter Nights from the [instructions]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72") at the bioware forums. (I tried the instructions on these forums but I wasn't able to get them to work)

It's running well, but at this point I'd like to have an icon on my desktop to launch it, and I can't work out how to do that.

To launch the game from terminal I use the following (starting in my home folder):
```
cd nwn
./nwn

```

This is pointing to a script in my nwn folder, and its contents are:
```

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

./nwmain $@

```

I can also just double-click on this file to run the game.

I've tried every way I can think of to create a launcher that points to this file, but I usually end up with something that does nothing at all when I double-click on it.

Any ideas on how to make this work?  I'm pretty clueless right now.

Thanks so much!

---

### Post by milton1 on 2007-08-25
add this to the top of your nwn file:

```
cd /home/yourHome/nwn/ 
```

replacing yourHome, etc with the path to the file

---

### Post by escape_goat on 2007-08-25
Awesome, that worked!  Thank you so much!  :)

---

