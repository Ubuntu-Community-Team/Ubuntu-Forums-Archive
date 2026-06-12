---
title: "[SOLVED] How to completely remove a program.Listen."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-15
I have a problem with a program,Listen.
I think it's the best audio player in Gnome.
But i can't reload it's library. When i click it,it s written "reload database" below but it doesn't.
I uninstall it(maybe it will be allright after reinstall) from add/remove or synaptic but it wasn't uninstalled completely.
The queue remains same,library and other options as well.
How can i remove it completely?

---

### Post by cubeist on 2008-01-15
In synaptic there is an option to remove completely.  You could try that.
or, what I like to do is use the locate command in the terminal and that will show where all the files are located on your HDD in case there is a persistent config file somewhere.
So, open a terminal and try:
locate listen
and see if it outputs anything.  Remember, don't delete anything you are not sure about! Especially from the system.

---

### Post by Rocket2DMn on 2008-01-15
In your home directory, there are hidden files and folders that start with a ".".  Open your home folder and hit CTRL+H.  There is probably a folder named after the program you used and uninstalled.  Delete that folder (.listen   ??).

---

### Post by rhc on 2008-01-15
Thank you very much.
Both of you.
I did both deleting ./listen folder and synaptic complete remove.
It worked like a charm.

---

