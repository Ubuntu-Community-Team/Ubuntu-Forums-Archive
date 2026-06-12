---
title: "Question of cli and programs"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by P235 on 2007-01-27
For Linux, are there any advantages to starting programs within an xterm and moving them to the background?  Like 'firefox &', 'evolution &', 'banshee &'?  They're all tied into the xterm because I can hit 'ps' and see these programs and their PIDs, but I know if I close the xterm without closing a program I've started on the foreground then things may go a little nasty - as in maybe a few panel apps will close.  But I've only closed xterm with maybe one program on the foreground...will nasty things happen if I close an xterm with a few programs on the background?  

If I click and run these same programs, an invisible xterm pops up for the programs?  Is that how it works?

---

### Post by riven0 on 2007-01-27
:confused: I'm not exactly sure what your talking about, but unless you opened an app through xterm, then you shouldn't have a problem. If you did open firefox through xterm, then exiting xterm will close down firefox, also.

> 
If I click and run these same programs, an invisible xterm pops up for the programs? Is that how it works?

xTerm is just the xorg terminal. It doesn't open with the programs. You can open a program with xterm, as I said, but it doesn't work the other way around. You use the terminal as an alternative to the GUI. I hope I'm explaining this right...

---

### Post by steve.horsley on 2007-01-28
The only advantage to running graphical programs in a terminal is that you get to see the error messages if it crashes. The disadvantage is that you have this terminal window cluttering up the desktop, and if you close it all your apps started from it will die instantly. So I would recommend not using a terminal - add a launcher to the menu, the panel, or to your desktop.

Using a launcher (or launching from nautilus) does not create an invisible terminal at all - it just launches the program directly rather than launching a terminal that launches the program.

---

### Post by Tomosaur on 2007-01-28
> **P235 said:**
> For Linux, are there any advantages to starting programs within an xterm and moving them to the background?  Like 'firefox &', 'evolution &', 'banshee &'?  They're all tied into the xterm because I can hit 'ps' and see these programs and their PIDs, but I know if I close the xterm without closing a program I've started on the foreground then things may go a little nasty - as in maybe a few panel apps will close.  But I've only closed xterm with maybe one program on the foreground...will nasty things happen if I close an xterm with a few programs on the background?  

If I click and run these same programs, an invisible xterm pops up for the programs?  Is that how it works?

Hmm not quite. You should think of the 'ps' command similar to Task Manager in Windows. PS is just another program, which allows you to see various processes and programs running on your machine ('top' works in much the same way). XTerm gives you an interface to talk to what is known as the shell. There are alternatives to xterm available, one being 'gnome-terminal'. They all work in pretty much the same way - Xterm itself is not running anything, the shell is. The shell is kind of like an intermediary layer between the core of the OS, and the GUI environment. Without the shell, nothing would work. If you get rid of X (which manages the graphics on Ubuntu), you'll be thrown into a virtual terminal when you boot up instead. It allows you to run various programs, but it is not XTerm (short for X-Terminal), which is a graphical terminal, which relies on X.

It can be pretty confusing to understand all this at first, but it begins to make sense when you boot into recovery mode or whatever. The system is perfectly capable of running without the GUI. Graphical programs rely on the X server running. If you boot into safe mode and try to run Firefox, you'll get an error message saying 'Could not find X' or something similar. The shell is always there - it's just X is running, and you need a window into the shell, such as XTerm, to play around with it. Thus, there's no need for an 'invisible XTerm' to be utilised, since the shell is always running anyway. Try thinking of X as a wall between you and the shell. Without a window through the wall (XTerm), you cannot use the shell.

You can test this all out by hitting Ctrl+Alt+F1 on your keyboard. This will switch to a 'virtual terminal'. Log in there, and you can play around in the shell. When you're done, type 'logout' or 'exit', then hit Ctrl+Alt+F7 to switch back to the X server.

---

