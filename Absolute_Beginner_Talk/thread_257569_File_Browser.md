---
title: "File Browser"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by uncleclinto on 2006-09-14
I have a folder (var/lib/moodle) that I need to be able to access from the file browser as an administrator in order to make modifications.  The desktop guide mentions opening "files with administrative privileges from the file manager", but that seems to be file-specific.  I need to be able to open a folder (and all of its subfolders) in the graphical file browser.  I'm sure it has something to do with chown and chmod, but I can't even find chown in the desktop guide, and I need very simplified instructions for the command-line challenged.

Is this to in-depth of a question for this NG?

---

### Post by mtron on 2006-09-14
no, just try "sudo nautilus" , and you will start nautilus with root access. you can do it this way with any other app.

cheers mtron

---

### Post by uncleclinto on 2006-09-14
Awesome!  I'm in!  Now if i could just find what I'm looking for.

---

### Post by mtron on 2006-09-15
try to be a bit more specific. what do you want to change or setup, what effect do you expect?

---

### Post by ChadMMc on 2006-09-15
Hi,
There is another way to do this because there are many times I will be in Nautilus in a specific location and have to open it in administrative (root) mode. 
I looked around and found the Nautilus scripting capabilities and found a good site for a bunch of scripts. [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)
one script in particular which you may find useful is the 'root-nautilus here' script which will open a nautilus window in the same location you are already in, but in root mode.

Hope this helps. :)

---

