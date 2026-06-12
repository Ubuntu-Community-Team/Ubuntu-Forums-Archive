---
title: "Start terminal and run command"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2008-03-23
Hey,

I want to create a file/shortcut that i can click that when i click it it opens up a terminal and runs a command, for example "echo hello". I want this terminal to appear in the window select list and to be useable. 

Saj

---

### Post by saj0577 on 2008-03-23
Also is their a way to automatically open up 3 tabs in teminal and enter a different command into each?
So i can click a file and a teminal opens with 3 tabs one with the command "echo hello" the second tab wit the command "echo "howdy" and the third with the command "echo goodbye".


Saj

---

### Post by codeslicer on 2008-03-23
That's easy - create a new file on your desktop and call it whateveryouwanthere.sh. Then, open it up with a text editor and add your commands. Save it. Right-click on that file and make it executable in the permissions tab. Now when you double click it you get a dialog asking what you want to do. Just click run in terminal...

---

### Post by Wolfan on 2008-03-23
Literally just make a text file with all the commands in it one command on each line and no file ext, then store it somewhere you have access to and give it executable rights.
Do this by right clicking on it going to properties then the permissions tab, then clicking "Allow executing file as a program" now you can build a lanuncher in the menu that points to that file.

---

### Post by saj0577 on 2008-03-23
Cheers for that :)

What about multiple tabs and multiple commands ?

Saj

---

### Post by codeslicer on 2008-03-23
Or here's something better: Create a launcher and add this inside: gnome-terminal -e "echo hello"

---

### Post by codeslicer on 2008-03-23
Try experimenting with the options.

```
gnome-terminal --help
```

and

```
man gnome-terminal
```

---

### Post by saj0577 on 2008-03-23
> **codeslicer said:**
> Or here's something better: Create a launcher and add this inside: gnome-terminal -e "echo hello"

Possible to add more then one command to a launcher?

i.e 
compiz --replace; amarok


would that work?

---

### Post by codeslicer on 2008-03-23
I think if you use a semi-colon(;) Bye, I have to go now cheers! :KS

---

### Post by saj0577 on 2008-03-23
Okay cheers il give it a go.
No problem

Saj

---

### Post by saj0577 on 2008-03-23
Semi colon did not work it says it could not open file

Saj

---

### Post by saj0577 on 2008-03-23
> **codeslicer said:**
> Or here's something better: Create a launcher and add this inside: gnome-terminal -e "echo hello"

The terminal closes immediately.

Saj

---

