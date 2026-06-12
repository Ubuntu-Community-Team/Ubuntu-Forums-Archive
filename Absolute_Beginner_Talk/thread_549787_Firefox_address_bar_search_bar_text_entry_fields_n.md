---
title: "Firefox address bar search bar text entry fields not selecting with ctrl+a"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by Derawk on 2007-09-13
In my installation of Firefox on xubuntu, I've got this issue where ctrl+a does not select all text within any given text entry field including the address bar, search bar, or the text box that I'm typing this message into. Instead it just moves the cursor to the far left of the current line. It works fine everywhere else.

Any known resolution for this?

---

### Post by finer recliner on 2007-09-13
thats kinda funny and odd.

ctrl+a in bash(aka in a terminal) does this by default. ctrl+e will move the cursor to the end of a line. there are many more, but that is obviously not the point of your post. sorry i cannot be of further help

---

### Post by Derawk on 2007-09-13
ctrl+e does indeed move the cursor to the far right of the line.

ctrl+v copies, ctrl+x cuts, ctrl+z is undo... ctrl+l puts puts focus on the address bar and selects all of it's text.

---

### Post by osx424242 on 2007-09-13
Ctrl+a and ctrl+e are emacs keys for beginning of line and end of line... could you have enabled an emacs emulation mode somehow (either in Firefox, with some sort of plugin; or in general on your system (for example, on my mac, ^a and ^e *always* go to the beginning or end of the line))?

---

### Post by finer recliner on 2007-09-14
osx42424242 is probably right. turn off all of your firefox extensions and see if the problem goes away. if it does, turn them back on one at a time until you find out which one is screwing with your keyboard shortcuts.

---

### Post by Derawk on 2007-09-15
It wasn't an extension. I'm not having this issue with Live CD, so I'm just going to start over with a fresh install of ubuntu.

---

### Post by kylez19 on 2007-10-03
I just setup firefox32 on a fresh ubuntu 64 feisty install. I am having the same problem, only i notice that when i press ctrl+a it DOES select all of the text, it just doesn't show the highlight. In other words, if i press backspace, it clears everything like it was all selected, only it doesn't appear that way. A problem that appears to be related to this is that any long url's the text just continues to display even past the end of the address bar. The same problem exists in form fields within an actual webpage in firefox. It functions correctly, but is just extremely hideous

Any suggestions?

---

