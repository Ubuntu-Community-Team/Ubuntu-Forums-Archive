---
title: "konsole / terminal /command line interface"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by punchy on 2006-03-21
Hello,

I really like the command line. With tab completion and the history which makes former commands easily recallable by using the arrows on your keyboard, its lean, clean and powerful.

However. I have not found a good way with which to open my CLI in the relevant directory immediately on openign. Its possible with 'krusader' (non Gnome native), a twopanel file manager, which will open the terminal in whichever directory my panel happens to be.

I have searched the forums, and I hope I simply haven't missed the relevant thread.

Please, whats the easiest way to have my konsole or terminal open in the directory I want which is at the moment relevant, without having to type my way to it using the 'cd' command ?

Thanks for your time!
Punchy

---

### Post by IYY on 2006-03-21
ROX Filer can do this without any configuration, but I imagine you don't want to use it (it's not as heavy on eye candy as Nautilus). There might be a Nautilus script to do what you want: try looking [here.]("http://g-scripts.sourceforge.net/")

---

### Post by colo on 2006-03-21
I don't use Nautilus or the like, but ROX-Filer, a really neat application based on GTK+ that presents files in a graphical manner. You can open a terminal-emulator (or any other program) of choice with the currently displayed location as CWD by pressing the "`"-Button. Don't know on how to do that in Nautilus or Konqueror, but if you happen to find out, please go ahead and tell me as well :)


(In the meantime, you can give ROX a shot ;))

---

### Post by trent dillman on 2006-03-21
heh... what's wrong with

```
cd /path/to/wherever
```

? :-P

---

### Post by punchy on 2006-03-21
Got the solution. Thanks for the tip, IYY, this is great. (trent: i have lots of files on my PC. I believe in orderign them, which leads to looong directory names. Stepping through them is a chore/bore. And I'm lazy. :) )

SOLUTION:

Any script which is placed in

/home/<YOURNAME>/.gnome2/nautilus-scripts/

will be visible if you rightclick into the nautilus filemanager and move the cursor to the third line from top, called 'Scripts'. Note, it has to be executable, and I needed to relogin (restart nautilus) to see it (use 'chmod' command).

I have put this simple script, called 'open-terminal-here.sh' into the directory. I got it off the www site linked by IYY above:

-----------

#!/bin/sh
#
# This script opens a gnome-terminal in the directory you select.
#
# Distributed under the terms of GNU GPL version 2 or later
#
# Copyright (C) Keith Conger <acid@twcny.rr.com>
#
# Install in your ~/Nautilus/scripts directory.
# You need to be running Nautilus 1.0.3+ to use scripts.

cd $NAUTILUS_SCRIPT_CURRENT_URI
exec gnome-terminal

---

### Post by trent dillman on 2006-03-21
Awesome. I was being cheeky anyhoo. I'm going to try this. :-D

---

### Post by peterpat on 2007-12-07
Ok not to confuse others, I tried that and it already really works by the solution.

---

