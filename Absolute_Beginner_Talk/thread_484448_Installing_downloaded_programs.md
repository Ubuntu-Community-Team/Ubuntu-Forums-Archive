---
title: "Installing downloaded programs"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by merlin114 on 2007-06-25
I'm brand new to Ubuntu and have pretty much got it set up okay.  I downloaded a Linux version of a commercial software package I use, but am having problems setting it up fully.  The download was a .sh file, which I finally figured out how to run, and it installed the software in /opt. 

The difficulty is this -- The program needed to save the serial number and registration key that I had to enter.  When I ran the software by clicking on it in the File Manager GUI, it accepted them, but then popped an error because I didn't have permission to save in the /opt folder.  When I ran the program using sudo from the terminal, it worked fine.  But it only runs when I do it that way - otherwise it hangs.  Also, the program doesn't show up in the Add/Remove area, nor in the Synaptic Package Manager.  I'd like to get it into the Applications menu.  Is there a way to make a script to launch the program with the sudo command so I don't have to do it from the terminal every time?  And how do I get the Applications Add/Remove to see the program (or the script)?  Thanks in advance!

---

### Post by BobCFC on 2007-06-25
If you want to add an item to the menus,  right-click on Applications and choose edit menu..

Then pick a category and click the New Item button - a form will pop up for you to fill in details.

If you click browse and find the binary you want to run it will put it in the command box.  You can also chose any .png file as an icon and give it a name.

If you want to run a program as root prefix the command box with **gksu** such as

gksu gedit

This will pop up a window which asks for your password each time you run it without needing the terminal.


You can also add items to the panel in a similar way by right-clicking in free space and choosing add to panel.   Or on the desktop right-click then Create Launcher.

---

### Post by merlin114 on 2007-06-25
Thanks a bunch.  That worked like a charm.  It looks so easy now, but the solution doesn't just jump out at you when your beginning.  Thanks again for the help.

---

