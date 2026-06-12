---
title: "newbie question!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by almostalive on 2007-09-12
hello,
when I'm in a directory, such as **/usr/programs**, how come when I right click in the empty space, the **Create Folder**, and **Create Document** options are darkened out (unclickable) ?
also, when I right click a folder/file, the **rename** and **Delete** options are darkened out.

I know how to do those actions in the terminal, but doing them on the GUI would be alot quicker / less trouble
I'm guessing it has something to do with file permissions? where can I change those settings?

thank you :) it's my 2nd day running Ubuntu

---

### Post by pissedoffdude on 2007-09-12
> **almostalive said:**
> hello,
when I'm in a directory, such as **/usr/programs**, how come when I right click in the empty space, the **Create Folder**, and **Create Document** options are darkened out (unclickable) ?
also, when I right click a folder/file, the **rename** and **Delete** options are darkened out.

I know how to do those actions in the terminal, but doing them on the GUI would be alot quicker / less trouble

thank you :) it's my 2nd day running Ubuntu

Try ```
gksudo nautilus
```

---

### Post by Beggar on 2007-09-12
Directories in which these options are grayed out, are directories to which your user does not have write permission. That is why if you try and add one using the terminal you need to use sudo.

If you run nautilus as root (see previous post) then you will be able to write to these directories, but I highly recommend avoiding that, because a root nautilus can delete any file, even ones you should never ever ever touch.

---

### Post by heinig on 2007-09-12
You need to be root to edit that, so open nautilus as root.. Alt + F2 and type "gksudo nautilus"

---

### Post by almostalive on 2007-09-12
hmm, ok thanks.

Is it possible to just give the user (me) write permissions so I don't have to log into root, so I can edit files whenever I want ?
or is doing that not recommended?

---

### Post by Technophobia on 2007-09-12
not recommended

Bookmark these two sites for future reference-

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) (install stuff)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) (will let you know about permissions and other admin tasks. May not be as useful as the guide)

---

### Post by diatribe on 2007-09-12
you can use 

sudo chown yourname /path/to 

to gain write access to directories

---

### Post by Beggar on 2007-09-12
> **diatribe said:**
> you can use 

sudo chown yourname /path/to 

to gain write access to directories

Unless you need to you should never do this to files outside of your home directory and other drives which you have mounted. Changing ownership of system files makes it much much easier to screw up your system.

---

