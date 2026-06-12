---
title: "running in terminal"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by spencewah on 2006-03-22
I've set my file associations for .sbg files to open with sbagen and they run as they should.  However, I'd like them to run in an open terminal window instead of behind the scenes (which is the way it works now).  What's the command for this?

---

### Post by Pragmatist on 2006-03-23
> Originally Posted by: **spencewah**
*I've set my file associations for .sbg files to open with sbagen and they run as they should. However, I'd like them to run in an open terminal window instead of behind the scenes (which is the way it works now). What's the command for this?*

Well that depends on how sbagen works.  Are you running a binary?  When you say "behind the scenes" what exactly do you mean?  Are you running it from a menu? From Nautilus or Konqueror?

If the program is just a shell script, then it is as simple as opening a terminal and typing the script name including the full path to its location.

If what your looking for is messages, that also is application specific an depends on how the program is designed.  It might be simple, it might be impossible.

---

### Post by spencewah on 2006-03-23
as it is right now if I open a terminal and type "sbagen FILENAME.sbg" it will run the file and display the output from the file's output.

If I choose to associate sbagen with .sbg files, the file still runs when I open it (through the GNOME file browser) but the terminal with the information doens't pop up.

---

### Post by Pragmatist on 2006-03-24
Two ideas:
1.) Create a launcher (a.k.a an Icon in Windows terminology).
Right-click on the panel, choose 'launcher' or 'custom application' or something similar (I'm not running Gnome right now so I can't be exact, but you should find it).  Your given the option of picking the item you want a launcher for, or choosing the program from your filesystem manually.  If you have the program on a menu, just choose it that way...in either event, once you have the launcher, you can Right-click and select properties, there you'll see a checkbox, on the screen containing the command to execute the file,...it says something like "open in a terminal".  Check that box and you should be good to go.

2.) Do it from a menu.  Here I have a way that should definitely work...I'm just not sure whether or not this is the standard approach.
Open an editor and call your file something memorable (I'm going to call it filename):
```
gedit filename
```
Type this in the file
```
 
#!/bin/sh


# A very simple script to run sbagen

sbagen


```
Save the file and exit the editor.
Then make this script executable:
```
chmod +x executable
```
Now, in the menu editor (you can run **smeg** from a terminal to open the menu editor). Where there is a place to enter the command to run the program put:
```
/bin/sh filename
```
In this case you'll have to give the full path to the filename unless you put the script in a standard place.  The standard approach is to make a "bin" directory in your home directory, place all your scripts there, and then make sure that $HOME/bin is in your path so it knows to look there when a command is run.  If your not writing several scripts, just put the full path :)

---

