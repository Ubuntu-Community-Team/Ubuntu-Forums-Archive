---
title: "download managers"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-08-22
is there a download manager for linux where I can request it to download specific files from websites.  for example can I filter pictures from everything else and download those pictures?

---

### Post by Rogue21121987 on 2005-08-23
Is something like this what you are looking for?

[https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Download%20Tools&numpg=10&id=201](https://addons.mozilla.org/extensions/moreinfo.php?application=firefox&category=Download%20Tools&numpg=10&id=201)

It's a plugin for firefox, I don't know whether it will work on ubuntu (I'm using portable firefox now), but give it a try.  It should work.

---

### Post by KingBahamut on 2005-08-23
apt-get install d4x 

=)

---

### Post by dvarsam on 2006-03-07
I downloaded the "d4x" Download Manager.

_I have the following problems_:

1. The program does NOT create a shortcut inside the "Applications" Menu...

2. Whenever I want to run the program, I have to launch a Terminal & type "d4x" 
    to use it.

3. The Terminal Window MUST remain open, for ALL the duration of the Download...


_Questions_:

1. Isn't there another Download Manager program out there for my Ubuntu, that 
    does NOT require the above?

2. IF not, then how can I add a "link" of the program "d4x" & put it in the 
    "Applications" menu?

Thanks.

---

### Post by Sweet on 2006-03-07
Try gwget, its designed for use with gnome.

It minimises to the tray and also appears on the application list when you install it :D 

```
sudo apt-get install gwget
```

---

### Post by Mustard on 2006-03-07
[QUOTE=dvarsam]I downloaded the "d4x" Download Manager.

_I have the following problems_:

1. The program does NOT create a shortcut inside the "Applications" Menu...

2. Whenever I want to run the program, I have to launch a Terminal & type "d4x" 
    to use it.

3. The Terminal Window MUST remain open, for ALL the duration of the Download...


_Questions_:

1. Isn't there another Download Manager program out there for my Ubuntu, that 
    does NOT require the above?

2. IF not, then how can I add a "link" of the program "d4x" & put it in the 
    "Applications" menu?

Thanks.[/QUOTE]

Assuming you are using Breezy Badger 5.10, you can add items to the Applications menu using the 'Application Menu Editor' in your Applications>>System Tools menu.  When you open this up you can create a new entry in your menu, under the subheading of your choice.  You can can create your own submenu by pressing 'New Menu' or you can add an new entry to an existing submenu by selecting the submenu in question, then pressing the 'New Entry' button. The 'Name' and 'Comments' feilds can contain anything you like.  They are basically descriptive fields. In the 'command' field for the new entry put the same command that you would use to start the application in terminal.  Don't tick the 'run in terminal' box, as this is not what you want it to do.

---

