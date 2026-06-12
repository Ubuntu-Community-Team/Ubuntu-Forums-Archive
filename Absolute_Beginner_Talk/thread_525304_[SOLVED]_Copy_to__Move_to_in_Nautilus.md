---
title: "[SOLVED] Copy to / Move to in Nautilus"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by conphara on 2007-08-14
Is there a similar function in Nautilus as there is in Konqueror, moving/copying files by right-clicking? Has someone made a script that I can download?

---

### Post by proalan on 2007-08-14
are you refering to the pop up context menu with the 'cut, copy, paste move to' options when you right click on a file in a folder?

It should be there and working.

---

### Post by conphara on 2007-08-14
No, that right-click menu is there. But  the function I'm talking about is when you right-click a file or folder in Konqueror you get at the bottom of the menu two functions copy to / move to. Those functions arrows themselves to a tree of the filesystem and the last used destination. I use this function in konqueror a lot, moving a lot of files.

---

### Post by Hospadar on 2007-08-14
There may be a nautilus extension for it, (or something like it) try poking around synaptic (all the extensions are named "nautilus-<something>")
Alternatively, you could always install konqueror (even in gnome) It should work just fine.

---

### Post by logos34 on 2007-08-14
> **conphara said:**
> Is there a similar function in Nautilus as there is in Konqueror, moving/copying files by right-clicking? Has someone made a script that I can download?

You don't need a script, there's a keyboard shortcut: hold down the Alt key and drag 'n drop the file from the main window to the destination dir in the side pane tree.  Select 'move' or 'copy'

---

### Post by conphara on 2007-08-15
Thanks guys, I'll try the keyboard shortcut (alt-key) and have my sharing folder in left pane. 

Case/Thread closed...

---

### Post by Arthur Archnix on 2007-08-15
Under thread tools, you'll find an option to close the thread as solved.

---

### Post by Sweet Mercury on 2007-08-15
> **logos34 said:**
> You don't need a script, there's a keyboard shortcut: hold down the Alt key and drag 'n drop the file from the main window to the destination dir in the side pane tree.  Select 'move' or 'copy'

That's a good tip. A lot of us ex/current Windows users are so used to the right-click and drag method to getting those context menus that when it doesn't work in Nautilus we are baffled.

---

### Post by juamez. on 2007-11-17
[http://ubuntuforums.org/showthread.php?t=535240](http://ubuntuforums.org/showthread.php?t=535240)

This thread states (and crosslinks to this one, lol!) that you can also use middlemouse button instead of ALT button to show the same context menu. Too bad it doesn't offer to "extract here" but whatever. Maybe this can be done by a script?

---

### Post by Bigbird999 on 2007-11-17
AM I missing something??  When I have nautilus open and press the Alt key, my cursor changes from an arrowhead to a hand and I can do is move the entire nautilus window around but I can't move files.  If I left click, I can drag 'n' drop to copy any file from the right side to any directory on the left side.  If I hold down the shift key, I move the file rather than copy.  This is exactly how windoze behaves,  Can sobody please 'splain this in newb friendly terms?

BB

BB

---

### Post by CatKiller on 2007-11-17
> **Bigbird999 said:**
> AM I missing something?

Yes. In normal usage, Alt acts as a modifier to move a window around. For the special case where you are dragging and dropping files from one window to another, Ctrl, Shift and Alt are modifiers for what action will be performed on those files.

I use the middle-click and drag so that I don't have to remember which button does what (I used right-click-and drag in Windows for the same reason) and I too miss the "Extract to here" option when using compressed files. Perhaps we should request it as a feature of Nautilus/File Roller?

---

### Post by Bigbird999 on 2007-11-17
Duh!!!!!!    I C now!!  You have to drag 'n drop then press Alt.  I was pressing down Alt B4 d'n'd.   But to me it sees easier just to d'n'd and then press shift to move or nothing to copy.  As for extract here, isn;t that added to the right click menu in windows by the program (winrar or winzip) modifying the registry key for the right click menu?  Iis there no equivalent to the "right click entries" registry key in Linux?

BB

---

### Post by CatKiller on 2007-11-17
> **Bigbird999 said:**
> You have to drag 'n drop then press Alt.  I was pressing down Alt B4 d'n'd.

Well, it's more drag-Alt-drop, but you've got the idea.

> Iis there no equivalent to the "right click entries" registry key in Linux?

I have absolutely no idea.

---

### Post by steve_waters on 2008-01-05
This is exactly what I was searching for.

There no registry key, but you can use nautilus actions to add extra right click functionality. You can use:

1. Applications --> Add/Remove....
2. Search for Nautilus Actions (and install it)

Then create commands that appear in the right click menu. There are some good examples on the forum, but I am happy with this drag-alt-select method. 

It was the main thing I did not like about Nautilus.

Good link below:

[http://ubuntuforums.org/showthread.php?t=417978](http://ubuntuforums.org/showthread.php?t=417978)

---

