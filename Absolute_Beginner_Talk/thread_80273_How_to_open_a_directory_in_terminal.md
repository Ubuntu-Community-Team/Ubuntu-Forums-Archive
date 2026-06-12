---
title: "How to open a directory in terminal"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by BoyOfDestiny on 2005-10-21
I download the nautilus open terminal script... didn't see the option... So I removed it...

One thing I noticed though, if you right click a folder, choose open with, custom command, type terminal, then the option will show up in the context menu from now on!

Can anyone tell me if there is a trick to enable scripts, and maybe what some of your favorite scripts are?

---

### Post by chanders on 2005-10-22
You need to place the script in 

/home/*YourHomeDirectoryHere*/.gnome2/nautilus-scripts

Make sure it has read, write and execute permissions on it. Now to open any 
folder in a terminal, right click on the folder and go to scripts, it should be there. 

Click on open terminal and that should open your folder in a terminal.

---

### Post by stoffepojken on 2005-10-22
If you installed nautilus-open-terminal and it does not work try killall nautilus

---

