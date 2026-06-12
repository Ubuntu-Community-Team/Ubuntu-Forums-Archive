---
title: "[SOLVED] Application Launcher / Space in Folder Name"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-12
I'd like to create an Application Launcher for a program I have but am having
a little bit of difficulty. I've typed the command path but it will not launch.
I am thinking it may be because I have spacing in the folder names.
Could someone tell me if that's the issue.  I think I have read somewhere
you have to place some kinda symbol between spaces.

/home/Me/My Programs/theprogram.exe

See the space (My Programs), is that why it won't work?

:KS

---

### Post by benx009 on 2007-08-12
try this:   */home/Me/"My Programs"/theprogram.exe*  (notice the quotation marks)

if the file really is an .exe file, then i would think that you'd need wine to run it.  in that case, try this: *wine /home/Me/"My Programs"/theprogram.exe*

---

### Post by Orbital75 on 2007-08-12
That Worked....... Thank you.  

Sorry, I should have put the correct extension.
The file is a .sh

---

