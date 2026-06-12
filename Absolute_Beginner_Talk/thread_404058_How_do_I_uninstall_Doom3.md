---
title: "How do I uninstall Doom3?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by leftybob on 2007-04-07
Wanting to try Doom3 on Ubuntu, I installed a package called "doom3-linux-1.3.1.1304.x86.run", along with the pkg files needed off the Doom3 (Windows) disk.
My computer turned out to be too slow for the game to be enjoyable, but now I don't know how to uninstall it.
How can I be sure I get all the files that were installed?
Thanks in advance.

---

### Post by ComplexNumber on 2007-04-07
when you downloaded it, did it have any instructions such as a file called 'README' or 'INSTALL' that made any mention about how to install and uninstall?

if noty, do you have a link to the actual package that you installed so that i can have a look at it myself?

---

### Post by leftybob on 2007-04-07
yes - it is [http://www.3dgamers.com/games/doom3/downloads/](http://www.3dgamers.com/games/doom3/downloads/)

---

### Post by ComplexNumber on 2007-04-07
hmmmm no other files. when you first ran the 'run' script, did it not give you an option to either install or uninstall?

other than that, i think that uninstalling it may be somewhat difficult if lots of files were installed.  unfortuinately, no clue is given as to whats installed from what i've read on that link.

are you wanting to just uninstall the executable, the menu item, or everything connected with the game?

---

### Post by leftybob on 2007-04-07
No, just to install.  A readme file was included, but only talked about how to get the extra files off the doom disc, and it made no mention of how to uninstall.
I should have stopped there, but I assumed the uninstall would be obvious later.
That was dumb.

---

### Post by leftybob on 2007-04-07
So am I out of luck?
Please let me know.
Thanks

---

### Post by ComplexNumber on 2007-04-07
hopefully someone else may know. it doesn't mean that you are out of luck, though.

---

### Post by leftybob on 2007-04-08
Should I just delete the Doom folder and the couple of entries in the local bin file?
Where else might I check for leftover files?
Thanks

---

### Post by trent dillman on 2007-04-08
...

---

### Post by leftybob on 2007-04-09
I believe I found just about everything using
```
sudo updatedb
locate doom3 | less
```
Thanks for your help Trent

---

