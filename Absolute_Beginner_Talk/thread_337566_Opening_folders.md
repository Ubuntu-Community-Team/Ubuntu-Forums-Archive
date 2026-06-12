---
title: "Opening folders"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-01-13
When I click on a folder, and then on a folder within it, both folders remain open.  The desktop then gets cluttered by all the open folders.  I would prefer to open new folders in the EXISTING open window, as you can do in WINDOWS.  Is there such an option?  I could not find it.  Even better, is there a "folders view" similar to what is found in WINDOWS, which shows the directory tree to the left of the open window that shows the files in the folder?

---

### Post by rai4shu2 on 2007-01-13
In Nautilus (which I assume is what you're using). You can change that behavior in the Edit > Preferences menu dialog. There's also an option for View > Side Pane for various types of views on the left side of the window, including a tree view if you want that.

---

### Post by floke on 2007-01-13
Ditto the above.

While viewing a folder in Nautilus, go Edit/Preferences/Behaviour and uncheck the box for 'Always open in browser windows'.

For more settings etc. open a terminal, type 'gconf-editor', then go 'Apps/Nautilus' and have a play around.

Have fun!

---

### Post by venik212 on 2007-01-13
Thanks, guys-- I broke down and read the manual, and found the 'Browser mode' choice, which is what I wanted.  Now if I knew how to make file associations stick, so I could click on a LyX file and have it open in Lyx, I could be happy (for the time being..)  I tried the Properties, but the effect (an open dialog) is not what I want.

---

### Post by hal10000 on 2007-01-13
In the file properties dialog (right-click) you can assign an apllication to be opened when clicking the file.

---

### Post by Pobega on 2007-01-13
Nautilus seems to do this by default, but as far as I know it is disabled in Ubuntu Edgy. Are you running Ubuntu or one of it's brothers, if Ubuntu did you ever uninstall/reinstall Nautilus?

---

### Post by venik212 on 2007-01-13
Thanks-- the Browser mode is what I wanted.

---

