---
title: "Add Gnome Run Dialog to Main Menu"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by jpietari on 2007-07-29
Does anybody know the command to open the Gnome Run Dialog?  I would like to add it to the Main Menu.  When I look in Gnome's menu editor, the app doesn't exist.

For now, I'm stuck using alt + F2, which is garbage.  I know it can be changed, but I don't want to get use to using a short-cut key that isn't standard (...maybe I'm just weird).

Thanks in advance!

---

### Post by kevinlyfellow on 2007-07-29
Looks like the command to set that up is gone, and has been integrated into the gnome panel.  How foolish... 

Here's some discussion here
[http://ubuntuforums.org/showthread.php?t=115974&page=2](http://ubuntuforums.org/showthread.php?t=115974&page=2)

---

### Post by jpietari on 2007-07-29
Thanks for your help.

These are the steps I took to add the gnome run dialog to the Main Menu:
1.  Opened the root terminal and installed the necessary libraries

**Command:**
apt-get install build-essential libx11-dev

2.  Download "gnome-run.c" from [http://gruyere.ucd.ie/~davide/gnome_run.html](http://gruyere.ucd.ie/~davide/gnome_run.html)

3. Go back to root terminal and compiled downloaded source code

**Command:**
gcc gnome-run.c -o gnome-run -L/usr/X11R6/lib -lX11

4.  While still in root terminal, move the binary to the user library directory

**Command:**
mv gnome-run /usr/bin

5.  Right-clicked the gnome Main Menu and select "Edit Menus"

6.  From the Main Menu (edit menu) dialog, click "New Item" and type the following parameters:

Type: Application in Terminal
Name: Run...
Command: gnome-run
Comment: Open Run Dialog

You're Done!!!!!!!!!

The reason I used "Application in Terminal" is so the dialog would have focus when it is open.  From the source code, I could not figure out how to set focus...

**References:**
[http://ubuntuforums.org/showpost.php?p=650010&postcount=18](http://ubuntuforums.org/showpost.php?p=650010&postcount=18)
[http://tronche.com/gui/x/xlib/event-handling/XSendEvent.html](http://tronche.com/gui/x/xlib/event-handling/XSendEvent.html)
[http://gruyere.ucd.ie/~davide/gnome_run.html](http://gruyere.ucd.ie/~davide/gnome_run.html)

---

### Post by X-Stranger on 2008-05-13
> **jpietari said:**
> Thanks for your help.

These are the steps I took to add the gnome run dialog to the Main Menu:
1.  Opened the root terminal and installed the necessary libraries

**Command:**
apt-get install build-essential libx11-dev

2.  Download "gnome-run.c" from [http://gruyere.ucd.ie/~davide/gnome_run.html](http://gruyere.ucd.ie/~davide/gnome_run.html)

3. Go back to root terminal and compiled downloaded source code

**Command:**
gcc gnome-run.c -o gnome-run -L/usr/X11R6/lib -lX11

4.  While still in root terminal, move the binary to the user library directory

**Command:**
mv gnome-run /usr/bin

5.  Right-clicked the gnome Main Menu and select "Edit Menus"

6.  From the Main Menu (edit menu) dialog, click "New Item" and type the following parameters:

Type: Application in Terminal
Name: Run...
Command: gnome-run
Comment: Open Run Dialog

You're Done!!!!!!!!!

The reason I used "Application in Terminal" is so the dialog would have focus when it is open.  From the source code, I could not figure out how to set focus...

**References:**
[http://ubuntuforums.org/showpost.php?p=650010&postcount=18](http://ubuntuforums.org/showpost.php?p=650010&postcount=18)
[http://tronche.com/gui/x/xlib/event-handling/XSendEvent.html](http://tronche.com/gui/x/xlib/event-handling/XSendEvent.html)
[http://gruyere.ucd.ie/~davide/gnome_run.html](http://gruyere.ucd.ie/~davide/gnome_run.html)

To make window focused you have to modify gnome-run.c in the next way: replace string
```
event.data.l[1] = (Time)0;
```
with
```
event.data.l[1] = (Time) time(NULL);
```
Then it will work correctly.

---

