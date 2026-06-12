---
title: "Creating a shortcut for a program...?"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by XtremeBlaze on 2007-12-12
I feel kind of stupid asking this because it's probably really easy. I accidentally deleted the shortcut icon for a program in my applications menu, thinking it would only delete the one shortcut when it deleted all of them, and now I don't know how to start up the program :confused:

Is there a way to create a shortcut for the application on the desktop using the terminal, or is there another way?

Any help is much appreciated :)

---

### Post by jken146 on 2007-12-12
Which program are you trying to run?

In Gnome, you can right click on the Applications menu and use Edit Menu to add/remove entries for individual programs.  You can also add launchers for programs to the desktop and the panels in a similar way.  You need to know the command that starts the program though.

---

### Post by XtremeBlaze on 2007-12-12
The program I'm trying to run is Cedega.

Is there a launcher in the program files? and if not, how do you make one in the applications menu?

---

### Post by jken146 on 2007-12-12
I've never used Cedega myself but it wouldn't surprise me if the command was ```
cedega
```  Try that in a terminal first to see if it works.

To make a launcher in the applications menu, right-click on it and choose Edit Menu.  Then find the button for adding a new program to the menu and fill in the info it asks for.  The command is the only bit that really matters.

Also, what do you mean by "Is there a launcher in the program files?"?

---

### Post by XtremeBlaze on 2007-12-12
It's just that I only recently made the switch from Windows to Ubuntu, and in Windows, in the program files there is a launcher for the application. Just wondered if Ubuntu had a similar thing....

I'll try what you said now ;)

EDIT in the terminal the command works :)

But how do you create the launcher in the applications menu. What do you type into the "Command" box so that the application starts, because when you type in either "Cedega" or "Cedega %U" it doesn't work :(

---

### Post by jken146 on 2007-12-12
Linux doesn't have a Program Files driectory as such.  Things are a little more spread out.  Most programs you install yourself can be found in /usr/bin.  The file names there should correspond with the command you need.

---

### Post by eolson on 2007-12-12
If the program is already installed,  

Click on Applications
left click and hold on the program
drag it to the panel and release the left click
your done.

---

### Post by jken146 on 2007-12-12
I think the OP lost his entry in the Applications menu.

---

### Post by eolson on 2007-12-12
MY bad!   I didn't completely read the post!   Sorry.   More beer should fix my problem.

---

### Post by thelatinist on 2007-12-12
1) Right-click on Applications > Edit Menus
2) Select the program group you wish to add the file to in the left pane.
3) Click + New Item
4) For "Name:" put Cedega and for "Command" put cedega (case is important).
5) Click "Okay."

---

### Post by XtremeBlaze on 2007-12-12
Thank you very much for your help, it worked :)

---

### Post by thelatinist on 2007-12-12
> **XtremeBlaze said:**
> Thank you very much for your help, it worked :)

Glad it helped.  Don't forget to mark this thread solved.

---

