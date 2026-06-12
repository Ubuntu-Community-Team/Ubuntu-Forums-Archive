---
title: "How do i write a GUI frontend to a command line program?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2008-01-11
where could i find a nice guide to writing a GUI frontend to a command line app?

ultimately, i'd like to make a GUI for Aircrack, since that program has always interested me, but i can't figure out the complicated  command line syntax.

---

### Post by Xavieran on 2008-01-11
1)Do you know much about gui programming?
2)Your first shots at GUI programming should probably be zenity (man zenity)(I have managed to write some pretty cool gui apps with it :))
3)Ask questions like this in the Programming sub forums,they are geared towards many people like you and the people in them usually know more about programming than here (no offense to anyone intended :)):)
4)Don't stop asking questions :)

The first thing to do is figure out the command-line syntax for aircrack-ng,then write a python or other script to simplify it (os.system is quite helpful doing this...)...once you have a script that can simplify things for the users add zenity to it to do the text based parts...then start learning pyGTK or the GTK library of your choice to simplify it even more...

---

### Post by Sonic Reducer on 2008-01-11
i originally put this in the Hot wo section, hoping someone could show me how to do this, but an administrator put it in absolute beginner. i'm assuming it goes here lol

---

### Post by marufaberlin on 2008-01-11
You might want to have a look at glade-2, there you can design a GUI pretty quickly and then assign callback functions. Define some variables in the callbacks (parameters), put them all together and then put something like this into the callback for a *run* button (or something similar):

system("aircrack-ng"); //and add the variables defined


marufaberlin

---

### Post by peabody on 2008-01-11
> **Sonic Reducer said:**
> 
ultimately, i'd like to make a GUI for Aircrack, since that program has always interested me, but i can't figure out the complicated  command line syntax.

If you don't figure out the commands, you'll never be able to write a gui front-end for it.  With aircrack-ng, I would honestly recommend focussing on making bash aliases and scripts to help automate the process.  I can't ever see any gui being able to give you adequate control of those programs.

I would start with nautilus scripts using zenity.  Work your way up, a little at a time.

---

### Post by marufaberlin on 2008-01-11
Why bash scripts? And why zenity?

---

### Post by Xavieran on 2008-01-11
Zeninty is *easy* to use...GUI programming is actually quite an involved process but zenity can make it fairly simple...BASH scripts because: you will be able to make a GUI much easier if you already have a general framework for executing commands...

---

