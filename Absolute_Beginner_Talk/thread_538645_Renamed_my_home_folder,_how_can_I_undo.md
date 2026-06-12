---
title: "Renamed my home folder, how can I undo?"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by Swarms on 2007-08-30
For some stupid reason I renamed my user folder, which made me unable to launch anything, like nautilus root to undo it. And I can't login either, is there a fix for this dear sires?

---

### Post by Obor on 2007-08-30
i think you could boot up into the safe mode and rename it back. Probably with the mv command i.e:

```
mv John Jack
```  	to Rename the folder "John" to "Jack" in the current directory.

Somebody correct me if I'm wrong...

> 
CREATING, REMOVING, AND MOVING DIRECTORIES

Use the commands below to create, move, or remove directories.

    mkdir   dirname
        Creates a subdirectory named dirname in the current directory. Fetch users can select Create New Directory from the Directories menu.

    rmdir   dirname
        Removes the subdirectory named dirname from the current directory. Fetch users can select Delete Directory or File from the Remote menu.

    mv   dir1   dir2
        Moves (renames) the subdirectory (and its contents) named dir1 to dir2. Fetch users can select Rename File from the Remote menu.
[URL="http://www.utexas.edu/learn/unix/"]
Source[/URL]

---

### Post by Swarms on 2007-08-30
And that did the trick! Thanks a lot!

Btw. atm. my user and laptop is called like this:
bear@toro-laptop, is there a way without reinstallingcalling it bear@bear-desktop?

---

### Post by Outrunner on 2007-08-30
You can edit the hostname here.

```
gksudo gedit /etc/hostname
```

---

### Post by Obor on 2007-08-30
> **Swarms said:**
> And that did the trick! Thanks a lot!

Btw. atm. my user and laptop is called like this:
bear@toro-laptop, is there a way without reinstallingcalling it bear@bear-desktop?

    * System -> Administration -> Network ->General Tab -> Host Settings -> Hostname: Specify the computer name

---

