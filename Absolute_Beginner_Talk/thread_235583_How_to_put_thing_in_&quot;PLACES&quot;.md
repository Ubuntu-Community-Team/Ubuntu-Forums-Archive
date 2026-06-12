---
title: "How to put thing in &quot;PLACES&quot;?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-08-13
How to put thing in "PLACES"?
I know about the menu editor and how you can edit the menu to add items to it.
However how does one edit the panels?

I want to put **Gnome-Commander** into the **PLACES** panel.
This where the Nautilus (Computer) is listed, I would like Gnome-Commander there also.
I looked at the Add to Panel, but it does not seem to list the **Places**.

So how do you add something to an existing panel?

---

### Post by em3raldxiii on 2006-08-13
I'm at work, so this is just a guess, but have you tried draging and dropping?  I know you can put stuff on the main bar that way, I thought maybe you might be able to drag it onto the menu that way.

---

### Post by gargoyle on 2006-08-13
To em3raldxiii,

I just tried it did not work. It would not carry it over to **Places**.

I have been trying to read up on Gconf but that does not seem to be the item to use either.

Guess I keep looking.

---

### Post by Buffalo Soldier on 2006-08-13
In your Nautilus, just drag the folder what you want into the Places sidebar.

---

### Post by gargoyle on 2006-08-13
to Buffalo Soldier.
Close but no cigar. It did create launch icon for it but it was not put into the **Places**, it was put next to the Firefox and Evolution icon.

I want to place it in the drop down menu for **Places.**
On the top bar are

**Application  Places   System**.

Under **Places** you have
Home folder
Desktop
------
Computer
Cd/DVD creator
-------
Network Servers
Connect to Network
------
Search for files
Recent Documents

How do I put in under **Computer?**? This where I want it.

---

### Post by CatKiller on 2006-08-14
It's not quite exactly where you want it, but if you go to the folder in Nautilus and go to Bookmarks -> Add Bookmark then you'll get the folder in Places under your home folder and desktop

---

### Post by Leonivek on 2006-08-14
> **gargoyle said:**
> to Buffalo Soldier.
Close but no cigar. It did create launch icon for it but it was not put into the **Places**, it was put next to the Firefox and Evolution icon.

I want to place it in the drop down menu for **Places.**
On the top bar are

**Application  Places   System**.




1. Open Nautilus.
2. Drag the Folder you want to the _left sidebar_ in Nautilus, **not the toolbar at the top of your screen**.
3. Done!  Click on "Places" on your [Applications | Places | System] menu bar and you will see it there.

Hope this helps!  :)

---

### Post by gargoyle on 2006-08-15
> **Leonivek said:**
> 1. Open Nautilus.
2. Drag the Folder you want to the _left sidebar_ in Nautilus, **not the toolbar at the top of your screen**.
3. Done!  Click on "Places" on your [Applications | Places | System] menu bar and you will see it there.

Hope this helps!  :)
With the actions you describe how does it know to put the gnome-commander program into the Places menu? As I move the item over it cause the various folder to be highlighted. However there is no folder that I can see that is name **Places**.
What am I missing here?

---

### Post by Leonivek on 2006-08-17
> **gargoyle said:**
> With the actions you describe how does it know to put the gnome-commander program into the Places menu? As I move the item over it cause the various folder to be highlighted. However there is no folder that I can see that is name **Places**.
What am I missing here?

Oh, I'm sorry! :oops: I was thinking you wanted to add a folder to the Places menu and not a program... my bad.  The Places menu are for "places" (or folders) on your system, not programs.

:idea: An alternative is to add a **Drawer** applet to your panel, which works like a menu, and you can add any programs you wish to your Drawer and place it anywhere on your panel.  I do this for my most common *infrequent *applications that I don't want on my panel and that I don't want to go searching through menus for.

---

### Post by Buffalo Soldier on 2006-08-19
> **gargoyle said:**
> With the actions you describe how does it know to put the gnome-commander program into the Places menu? As I move the item over it cause the various folder to be highlighted. However there is no folder that I can see that is name **Places**.
What am I missing here?

Please refer to the picture attached.

---

### Post by Perfect Storm on 2006-08-19
You're so paedagogue-ish with your drawings, Buffalo Soldier :mrgreen:

---

### Post by gargoyle on 2006-08-19
To Buffalo Soldier,
In your image you are showing moving a folder, I do not wish to move a folder into Places but rather the program or executable item (gnome-commander) into Places.
This is the start point from the propreties of the gnome-commander executable.
**/usr/bin/gnome-commander**
If I try dragging it into the area you show the folder Third party it just snaps back and nothing is copied or placed into the area.

It seem like you can not copied executables into the area.
By the way I was doing it from sudo nautilus and not a plain user Nautilus.

I also attempt it by making a link and copying it over but that did not work either.

What now? Any more ideas?

---

### Post by Leonivek on 2006-08-20
This thread may help you:
[http://ubuntuforums.org/showthread.php?t=207021](http://ubuntuforums.org/showthread.php?t=207021)

---

