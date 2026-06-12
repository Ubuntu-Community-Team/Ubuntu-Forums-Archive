---
title: "Configuring the bash shell"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-14
How do I customize the bash shell so that it always stays on top and stays the dimensions and desktop position I set the next time I launch it. Also, how do I store common commands that I use over and over again. Right now, I'm keeping them on gedit and copy/paste them into bash. Thanks.

---

### Post by heimo on 2007-04-14
To open at specific position and size, use geometry flag. Eg.
```
gnome-terminal --geometry 60x20+250+200
```

For even further control, use devilspie (search forum for examples):
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)

For common commands,  create aliases and put them in your ~/.bashrc file or .bash_aliases (and uncomment couple lines from .bashrc). Syntax is very simple, for example:
```
alias ll='ls -l'
```
and now ll = ls -l

---

### Post by jacatone on 2007-04-15
Sorry, I'm not understanding this Devilspie. I found the terminal dimensions and position of: gnome-terminal --geometry 60x10+250+50 looks good. How do I install this devilspie to save that position and "always on top" when I launch the terminal? Thanks.

---

### Post by freebird54 on 2007-04-15
I think you will find that the previously used commands are 'automatically' stored in ~/.bash_history for you already.  Thus they should be accessible by means of up arrow, or various search methods.  Perhaps this link will show you a few options..

[http://www.talug.org/events/20030709/cmdline_history.html](http://www.talug.org/events/20030709/cmdline_history.html)

Keeping it handy I know not :)  (I just pop one up whenever I need it - it's always running).

---

