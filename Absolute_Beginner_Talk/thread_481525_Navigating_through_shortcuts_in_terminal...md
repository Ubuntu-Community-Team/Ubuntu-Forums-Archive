---
title: "Navigating through shortcuts in terminal.."
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Jyncus on 2007-06-22
This might be a really dumb question, but is it possible to "cd <name of launcher>" in a terminal to take you to the launcher's URL?  If not, if you have a really "deep" directory that you want to reach often and quickly in the terminal, what would be the best way to do so?  
: x

---

### Post by Orochi on 2007-06-22
I'm not sure I completely understand your question, but now matter how "deep" the directory is you can always get there in 1 command:
cd /dir1/dir2/dir3/dir4/etc

If you use it a lot and don't want to retype, just press the up key at the terminal prompt to go backwards through your entered commands until you see it again and press enter. 

Alternatively you could set up an alias command like 'alias dirshortcut="cd /dir1/dir2/dir3/dir4/etc"' so then typing dirshortcut would change your current working directory to the directory you want. Add the alias to your ~/.bashrc file and it'll work every time you start up terminal.

---

### Post by Jyncus on 2007-06-22
> **Orochi said:**
> I'm not sure I completely understand your question, but now matter how "deep" the directory is you can always get there in 1 command:
cd /dir1/dir2/dir3/dir4/etc

If you use it a lot and don't want to retype, just press the up key at the terminal prompt to go backwards through your entered commands until you see it again and press enter. 

Alternatively you could set up an alias command like 'alias dirshortcut="cd /dir1/dir2/dir3/dir4/etc"' so then typing dirshortcut would change your current working directory to the directory you want. Add the alias to your ~/.bashrc file and it'll work every time you start up terminal.

Indeed, it does only take one "cd /path/to/the/dir" command, I suppose I'm just not all that comfortable with wildcards yet, and so it takes me a really long time to get to the dir I'm trying to reach if I end up typing each folder all the way out..  

I thought I may be able to simply put a launcher in my home folder, fire up a terminal, and navigating immediately to the launcher's URL just by typing the name of it or something.  *shrug*  Nevertheless, your suggestion for setting up an alias command is exactly the kinda solution I was looking for - that'll work great.  =]
Appreciate it

---

### Post by steve.horsley on 2007-06-22
Remember that you can use the tab key to complete filenames - that saves time.

As Orochi says, you could create an alias.

Or you could make a symbolic link to the directory. You can do this by commadn line with the command:
**ln -s very/deep/directory/name/that/you/dont/want/to/keep/typing shortname**
or drag the folder to your home folder using 2 nautilus windows and the **middle** mouse button and choose **link here** at the popup menu.

---

