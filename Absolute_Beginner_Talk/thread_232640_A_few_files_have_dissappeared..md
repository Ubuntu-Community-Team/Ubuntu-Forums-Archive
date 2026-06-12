---
title: "A few files have dissappeared."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Nathan Otis on 2006-08-09
Greetings all. Feel free to move this topic if it fits better elsewhere... It sure seems like a beginner problem, though.

I downloaded a few files this evening. Then I started to rename them for my own purposes. The first one was fine. But the folder (not my whole (Ubuntu)  PC) locked up when I tried to change the second filename. I had to force the window to close.

When I open the folder now, the status bar shows 16 files, but I can't see them. This behavior persists after several restarts.

??!!,
n.

---

### Post by bscbrit on 2006-08-09
Which desktop are you using? xfce, Gnome, KDE, Enlightenment?  What were you renaming the files to?  Are the files visible using the command line?

---

### Post by arjun.shankar on 2006-08-09
Have you tried seeing what shows up in the terminal when you see the directory listing?

If you aren't comfortable using the terminal as yet, here is what you should do:

Click on Applications -> Accessories -> Terminal

Once it opens up, you are going to be in your home directory:
**/home/something**

Now use the 'cd' command to navigate to the directory with the problem:

**"cd /abc/def/ghi"** ;note that you must replace /abc/def/ghi with the path to your directory.

Then give the command: "ls -la"

This will show what all is there in that directory.

If you already know how to do this, you obviously didn't need the instructions. ;)

---

