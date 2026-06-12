---
title: "How do I edit and save configuration files"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Bunyak on 2006-09-01
stupid question.....

I think I have found a solution to a pppoe problem.  The solution involves editing lines in \etc\networking\interfaces.  My problem is that when I open the config file in a GUI-based text editor, I am informed my changes cannot be saved because I have insufficient privelige (I am the administrator).  I gather I need root priveliges to save my edits.  After reading the desktop guide again, I noticed that for configuration files, only a terminal-based text editor can be used.

so...How do i start a suitable terminal-based text editor that will give me sufficient priveliges to save changes to a configuration file?  Then, how do I open and save said file from that text editor?  Or, are there other ways to skin the cat?  I'm all ears.  :D

---

### Post by Anonii on 2006-09-01
You will use the terminal:
If you like a GUI editor use the following command:

_gksudo gedit /etc/networking/interfaces_

if you want a command based editor use:

_sudo nano /etc/networking/interfaces_
With nano you can save your progress with "Ctrl + X" then "Y" to accept the configurations you did.

Both are easy to use, and great.

---

### Post by Bunyak on 2006-09-01
Thanky thanky....will try as soon as I can.

---

