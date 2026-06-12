---
title: "some KDE software menu shortcut gone"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2008-01-05
there was hard disk error, but solved by fsck.
after i ran fsck and restarted, my kde software all gone, i'm using gnome ubuntu and i installed some kde software.
i went to Add/Remove Application to see whether all the software are still there or not, and all the software seems to be still there. and i can run it using Terminal.

my theme also slightly changed to simpler theme, affects only the minimize/close button or the row (sorry i donno how to mention it).
so i decided to go to appearance option, but seems that i hide it. to unhide it, i went to "Edit Menu", but i can't open it.

besides, my gconf-editor configuration reset too, but easily solved by running gconf-editor.

i think the problem can be solved if i can run the Menu Editor, anyone knows the command?

---

### Post by Xavieran on 2008-01-05
Right click on your menus and select edit menus...
Then simply add in the KDE apps that went missing by clicking the appropriate Menu and selecting add item...the launcher will be the command you used to run it in the terminal...:)

---

### Post by oliviacond on 2008-01-05
> **Xavieran said:**
> Right click on your menus and select edit menus...
Then simply add in the KDE apps that went missing by clicking the appropriate Menu and selecting add item...the launcher will be the command you used to run it in the terminal...:)

i can't. anyone knows the command?

the Human windows border seems to be gone.

edit: OK, i found the menu editor at /usr/share/applications, the kde applications gone even in the menu editor.

---

### Post by oliviacond on 2008-01-05
kde applications gone.

---

### Post by Xavieran on 2008-01-05
It should say add new on the left...

If it doesn't try reinstalling one of the KDE apps and then see if it appears in the menu...

---

### Post by oliviacond on 2008-01-05
reinstallation does the work=)

the alacarte still can't be started from panel, perhaps complete reinstallation can solve it.

---

