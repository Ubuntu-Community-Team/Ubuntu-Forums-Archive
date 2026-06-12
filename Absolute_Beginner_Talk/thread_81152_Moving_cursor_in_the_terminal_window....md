---
title: "Moving cursor in the terminal window..."
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by aeroRunner on 2005-10-23
This may sound like a completely stupid question, but its driving me crazy.  I can't seem to move the cursor in the terminal window with the mouse.  I think this has just started, because I don't ever remember having this problem before.  For example, say I type a line of something and realize that I have a typo near the beginning.  Well I would like to use the mouse to reposition the cursor where the typo is so that I can fix it.  But I can only move the cursor with the arrow keys.  Is this normal or did I inadvertantly change a setting or something?  Thanks.

---

### Post by Kyral on 2005-10-23
You mean the typing "point" or the mouse cursor arrow?

EDIT: I'm an idiot, you said the point.

EDIT: I don't think you can move the point...I don't think I ever have been able to...

---

### Post by SilentCacophony on 2005-10-23
The only thing I know of that might allow that is the **gpm** package. I'm not sure if it gives that exact functionality, though. You can check that out via synaptic. If it's installed already, then you might try to 

sudo dpkg-reconfigure gpm

or remove/reinstall it.

---

### Post by wmcbrine on 2005-10-24
There might be a terminal-based editor that lets you move the cursor with the mouse, but I haven't seen it.

gpm is for supporting mouse input on the text console (Alt-F1, etc.). Similar facilities are available in X-based terminal emulators like xterm, Gnome Terminal, etc.; but they don't use gpm. (Actually I believe gpm was written to emulate the mouse support of an xterm.)

While few terminal-based programs actually support the mouse, you can always use the mouse to copy and paste. When you're in terminal-based programs that do have mouse support, you have to hold the shift key while copying or pasting.

---

### Post by heimo on 2005-10-24
How about moving backwards and forwards using... not the arrow keys, but for example
[LIST]
[*]ctrl+A (to the beginning of line)   
[*]ctrl+E (to the end of line)   
[*]alt+B (back one word)   
[*]alt+F (forward one word) [/LIST] Other useful combinations:
[LIST]
[*]ctrl+W (delete word on left)   
[*]ctlr+K (delete end of line) [/LIST]

---

