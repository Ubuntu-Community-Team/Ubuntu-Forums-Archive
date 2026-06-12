---
title: "Quick question - how do I get the panel back?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2008-01-14
Any idea how I get the panel back - the one at the top, with the applications, time, etc.  I appreciate I won't get my original settings.  I'm sure there's something I can do in terminal, but now I've lost the top panel I can no longer get into that.  I've tried clicking and right-clicking on the desktop, but to no avail.  Thanks!

---

### Post by vojtech.t on 2008-01-14
Try this:

*gconftool-2 --recursive-unset /apps/panel*

and the restart he panel

*pkill gnome-panel*

---

### Post by useResa on 2008-01-14
I am not 100% sure about this, but AFAIK you can get the panel back by opening a terminal (press <Alt>-<F2> and issue the command *gnome-terminal*) and in the terminal issue the command
```
gnome-panel &
```

You could even try immediately (in the window that opens when pressing <Alt>-<F2>) the command *gnome-panel*

---

### Post by getmeoutofhere on 2008-01-14
gconftool-2 --recursive-unset /apps/panel

destroyed the botton panel, where the minimised programs are.  So my desktop is now pretty unusable.  Can only access programs via alt-f2.

gnome-panel &

didn't seem to do anything.

Any ideas?

Thanks.

---

### Post by getmeoutofhere on 2008-01-14
sudo debconf gnome-panel

seems to fix it, after a reboot.

I don't know what would have happened if I had rebooted without this command.

---

### Post by anaconda on 2008-01-14
ööhh..
usually the easiest way to add a new panel is to right-click on the existing panel and selecting "new panel"

Then just add all the launchers etc to that panel..

---

### Post by getmeoutofhere on 2008-01-14
Yes, but if you type 'delete this panel' the panel disappears, and you've no longer got a panel to click on.  My panel had some piece of corruption, that wouldn't go away, and I wanted to remove it and start again.  

While I found it relatively easy to find the solution, thanks to the Ubuntu forums, it's little things like this that demonstrate that Ubuntu probably isn't ready for the mass market. Can the man or woman in the street be expected to go onto the internet, find the right command, and put it in the terminal?  

Although I really like Ubuntu, I think that even an above average computer user  (maybe the second decile) would find it difficult to use without the forums.

---

### Post by Dragon43 on 2008-01-14
IMHO, that is the 'Beauty' & the "Beast' of the Open Source world.  Too many different OS, each with a a slightly different way to do things.  Not one is big enough by itself to cause a person to write a " Linux For Dummies" book.  that is a lot of work to do for free and it would need updates daily.  Forums are the best solution so far with the state of the comunity.

We need to tahnk the guys who answer our 'Absolute Beginners" questions because most of them are far above this level and I'm sure the constant going back over stuff gets old.

---

### Post by philinux on 2008-01-14
If you ctrl alt backspace then login again, according to this the system starts with one panel. You can then right click and add your other. You may have to reboot.

[http://www.gnome.org/learn/users-guide/2.8/ch02s02.html](http://www.gnome.org/learn/users-guide/2.8/ch02s02.html)

---

