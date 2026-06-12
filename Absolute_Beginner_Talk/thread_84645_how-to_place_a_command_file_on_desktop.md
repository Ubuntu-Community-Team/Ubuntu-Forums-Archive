---
title: "how-to place a command file on desktop"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by susa on 2005-10-31
I have a command I need to run every day and wish to place a shortcut to my desktop

this works but I wonder is there a better way, please post steps

1. create a new file "runme.cmd" on desktop
2. open in text editor (I use KEdit)
3. enter the command string(s)
4. access properties and make it executable

now I get a prompt every time I click it, asking me if I want to run the file, I click Ok or Yes

---

### Post by ubuntumaneh on 2005-10-31
Try inserting on the first line of runme.cmd:

#!/bin/bash

---

### Post by stuporglue on 2005-10-31
If that doesn't work for you, you can right click the desktop and choose "Create Launcher". You can drag this launcher to somewhere more convenient than the desktop too if you like...such as the toolbars or somethign.

---

### Post by susa on 2005-10-31
ok, that works fine

if I may follow-up on a related note, is there some easy way for me to create a text file shortcut on my desktop, I've tried "Notes.txt" but it ends up being opened by a terminal when I want it to default to KEdit or KWrite

basically, I want to be able to create small file snippets and just drop them into any "default" filename.txt and when that is later clicked, I want KEdit or KWrite (or any other default text editor) to open these

I guess I'm asking how to associate easily new filenames?

---

### Post by susa on 2005-12-15
no idea about text file association(s) ?

---

### Post by Mustard on 2005-12-15
[QUOTE=susa]no idea about text file association(s) ?[/QUOTE]
Hmm..not too sure how to do it in KDE.  It does it by default in Gnome.  I'm curious why it would go to terminal in KDE.  Does this text file have executable permissions?

---

### Post by bscbrit on 2005-12-15
I assume that you are using KDE for your desktop (and if I am wrong then I am even more confused than I thought!).  However, does this link help?

[http://lists.rpath.com/pipermail/distro-list/2005-January/000192.html](http://lists.rpath.com/pipermail/distro-list/2005-January/000192.html)

---

