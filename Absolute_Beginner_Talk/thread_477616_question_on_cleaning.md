---
title: "question on cleaning"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by gprok on 2007-06-18
Im new at linux and i was wondering if there is some kind of cleaning program that i could use to clean and wipe suff on the HD that is obsolete ??? i have a folder called LOST N FOUND which have like 450 mg in there and im not quite sure that this is very useful or just eating up space on my EXT3 drive.......Thanks a lot !!!

GProk:popcorn:

---

### Post by rikbrown2k on 2007-06-18
/lost+found is basically where Linux recovers files that may have been lost from hard disk errors (for example if the computer was turned off without being shut down properly).  If there's nothing in there that is useful to you, it's safe to delete the entire contents of that folder.

Also check out the /tmp folder, which is usually safe to delete as it just contains stuff like recently downloaded files where you just pressed "Run this file" and what not - same as Temp on windows really!

---

### Post by gprok on 2007-06-18
i got this whe i try to open or erase lost N found::::::

You do not have the permissions necessary to view the contents of "lost+found".


what should i do ???? TIA !
Gprok

---

### Post by rikbrown2k on 2007-06-18
It's because the folder is a system folder.  You need to delete it using the "sudo" command you may have used before - it basically gives you administration privileges (you don't get these by default for security reasons).

Open a terminal, and type

```
sudo rm -r /lost+found
```

the rm command is the console-way of deleting files, and the "-r" argument tells it to delete all subfolders too.
by putting sudo before, it'll give you superuser privileges - so you can delete this system folder (you'll be prompted for your password).

EDIT: if you just want to look in the folder, you could type ```
sudo nautilus
``` to open the gnome file manager as an administrator - so you can see the contents of the folder.  You could also delete it in that too.

---

### Post by gprok on 2007-06-18
thanks a lot Rik !!!!! very useful command......gotta learn those..hehehe


Gprok

---

### Post by rikbrown2k on 2007-06-18
No worries!

well, few basic console commands you'll find useful (may even speed up your day ;))

**cp <source> <destination>** copies <source> file to <desination>.  If you want to copy folders, use the "-r" recursive option.  Also **mv** moves the files instead.
**rm <file/directory>** removes the files.  Again, adding "-r" after "rm" as you did before will recursivly delete subfolders and files.
**mkdir <directory>** will create that folder.
**cat <filename>** will display the contents of that (text) file to the console.

Also, you can install packages by the console, you might've done this - a lot of Ubuntu/Debian guides will give instructions like this, using the **apt-get** program (this has to be run with sudo, as it needs administrative privileges), for example
```
sudo apt-get install kmess
``` would install KMess if it wasn't already installed.  Equally, replacing "install" with "remove" would get rid of it.

Have fun!

---

