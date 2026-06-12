---
title: "Open programs from terminal"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by pwaustin on 2005-09-23
Ok, total noob here, but here it goes.  I installed Firefox from downloading the tar file from the mozilla website and installing it.  It opened just after install and worked fine, but it did not get added to my list of programs in Kubuntu (in the Internet heading), so I'm not sure how to open it now.  I noticed this with other programs that are installed from the terminal also, they don't get added to the "Start" menu.  So how do I open programs like this?

---

### Post by karuptdata on 2005-09-23
You should be able to open terminal and simply type in firefox and it shouldl launch it if installed properly!

---

### Post by pwaustin on 2005-09-23
No, that doesn't work, it just says "command not found".

Also, is there a way to add programs to the list of programs in the start menu, so I don't have to open in terminal each time?

Thanks!

---

### Post by mneptok on 2005-09-23
[QUOTE=pwaustin]Ok, total noob here, but here it goes.  I installed Firefox from downloading the tar file from the mozilla website and installing it.  It opened just after install and worked fine, but it did not get added to my list of programs in Kubuntu (in the Internet heading), so I'm not sure how to open it now.  I noticed this with other programs that are installed from the terminal also, they don't get added to the "Start" menu.  So how do I open programs like this?[/QUOTE]

You should use apt-get whenever possible to install software. Often apt will create menu items for you.

---

### Post by gord on 2005-09-23
theres a large chance that you did not 'install' firefox properly if when you type 'firefox' at the terminal, it gives an error like that. 

you should 'sudo apt-get install firefox', unless you want the latest version. to get the latest dearpark build (1.5 beta) you just have to goto the directory you un-tar'ed it to, and type "./firefox"

---

### Post by pwaustin on 2005-09-23
Yeah, that's what I wanted to do and tried sudo apt-get install firefox.  Here is the message I got:

"Package firefox is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted,  or is only available from another source.

E: Package firefox has no installation candidate"

I don't understand what is going on here, and read in the forums that another way to install it is straight from the Mozilla website.

Any ideas on what this means?

---

### Post by fordfan753 on 2005-09-23
You probably installed firefox to a non auto directory.....try "whereis firefox" it should tell you where the actual file it. It might be in /sbin/ for example.

To add a new item to the Applications menu you will need a package called Smeg. It is in the Breezy repositories, and can be installed on Hoary.

---

### Post by pwaustin on 2005-09-23
when I try whereis firefox it just outputs 
"firefox:"

Thanks for the tip on Smeg, looks useful.

---

### Post by Kvark on 2005-09-23
[ deleted ]

---

### Post by fordfan753 on 2005-09-23
[QUOTE=pwaustin]when I try whereis firefox it just outputs 
"firefox:"

Thanks for the tip on Smeg, looks useful.[/QUOTE]

Try
```
locate firefox
``` 
If you installed firefox correctly that should pop up heaps of entries.

---

### Post by pwaustin on 2005-09-23
Yeah, also tried that first too, in Synaptic. mozilla-firefox is there, but when I click install, nothing happens (the box doesn't get checked or anything).

The same thing is happening when I try to install Gaim through Synaptic.

---

