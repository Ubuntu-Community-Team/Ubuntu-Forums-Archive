---
title: "A few terminal commands"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by soul814 on 2007-02-25
I installed ubuntu on my desktop to test around and get use to it before I install it on my notebook and so far its amazing. Aside from failing to get beryl working, and not understanding how tar.gz etc work, everything is going fine. The thing that annoys me the most has to be with root. Is there any way to log in directly into root? I found the command

> gksudo nautilus root

but it's annoying to type it every time to delete a file / folder. Oh yea, is there a command to change permissions of files through terminal (using chmod?)

Another question, whats the difference with just extracting a tar file using the GUI thing as opposed to going into terminal and typing tar someletters etc. I found that to be confusing when installing / upgrading gaim, java. I had no clue what I was doing just copying and pasting. 

Another question, the directories seem confusing to me. I don't understand the structure. 
/usr/lib/ would be window's Local Settings I suppose right?
What is /var/ as I see apache's default directory is located there
/bin/ and /lib/ are the "windows and system32" directories?

Thanks for your help

---

### Post by aysiu on 2007-02-25
If you create a launcher or, better yet, a keyboard shortcut for ```
gksudo nautilus
``` it's not as annoying:
[http://doc.gwos.org/index.php/GnomeKeyboardShortcut](http://doc.gwos.org/index.php/GnomeKeyboardShortcut)

There's no significant difference between extracting archives with the GUI and terminal. The terminal gives you more options, but the end result is more or less the same.

As for the directories, read this:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by zvacet on 2007-02-26
You can download nautilus scripts with Automatix.To use them just right click and you see dropdown menu and scripts aer there.

---

### Post by STREETURCHINE on 2007-02-26
yes i have the nautilus script from automatix it is a godsend,lol handy as well:)

---

