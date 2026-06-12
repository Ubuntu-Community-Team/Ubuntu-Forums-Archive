---
title: "How to execute Nautilus Scripts"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2007-01-04
I am trying to implement a Naulilus Script (from [http://doc.gwos.org/index.php/Gedit_as_root)](http://doc.gwos.org/index.php/Gedit_as_root)). I have followed the instructions pretty carefully - but Nautilus does not seem to call the script.

ie I have -
Created a script  ~/.gnome2/nautilus-scripts/gedit-root

Made it executable with chmod +x ~/.gnome2/nautilus-scripts/gedit-root

The first thing that is obvious is that nautilus-scripts is not on my path. If I type

PATH=~/.gnome2/nautilus-scripts:${PATH}

(I don't understand that, but copied it from .bash_profile), I can now call my script by 

~/.gnome2/nautilus-scripts/gedit-root

which seems to work perfectly. But not from Nautilus.

Question 1 is what am I doing wrong and Question 2 (related) is how do I get that PATH command to execute on start up? I have tried putting it into .bash_profile but it does not seem to work.

---

### Post by cairnsww on 2007-01-04
OK - The answewr to question 1 was that I should not spell Nautilus Nautalus. It does not work.

So my script works perfectly.

But Question 2 still stands - how can I set a path on start up?

---

### Post by bigken on 2007-01-04
you could have installed automatix this would install the scripts for you ;)

---

### Post by cairnsww on 2007-01-04
Sure I could have - but then I would not have learned anything.:-D 

What I have learned so far is that Nautilus does not need its directory on the path.

I have also learned that I don't understand paths and start up scripts...

---

### Post by bigken on 2007-01-04
> **cairnsww said:**
> 
I have also learned that I don't understand paths and start up scripts...

me either lol :)

---

