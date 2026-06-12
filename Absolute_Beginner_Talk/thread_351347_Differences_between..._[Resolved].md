---
title: "Differences between... [Resolved]"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Armor on 2007-02-01
What's the difference between nano, sudo, gksudo?
For example: I want to edit my xorg.conf, what should I do?

"gksudo gedit /etc/X11/xorg.conf"

or

"sudo gedit /etc/X11/xorg.conf"

or

"nano gedit /etc/X11/xorg.conf"

or just "nano /etc/X11/xorg.conf"

??

---

### Post by aysiu on 2007-02-01
Read this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

```
gksudo gedit /etc/X11/xorg.conf
``` This is good. Since *gedit* is a graphical program, you use *gksudo* with it.

```
sudo gedit /etc/X11/xorg.conf
``` This is bad. Since *gedit* is a graphical program, you shouldn't use *sudo* with it.

```
nano gedit /etc/X11/xorg.conf
``` This makes no sense. *nano* is a text editor and *gedit* is also a text editor. Pick one or the other. You can't use both in the same command like that.

```
nano /etc/X11/xorg.conf
``` That's fine, but you won't be able to save changes, since /etc/X11/xorg.conf is a system file. You need *sudo* for that: *sudo nano /etc/X11/xorg.conf*

---

### Post by Armor on 2007-02-01
What does the "gk" mean? Example: gksudo gedit vs sudo gedit?

---

### Post by aysiu on 2007-02-01
> **Armor said:**
> What does the "gk" mean? Example: gksudo gedit vs sudo gedit?
I'm not sure of the exact origins of the command, but I would imagine it has something to do with Gnome using the GTK toolkit; though, there isn't an exact parallel (since KDE uses QT and the corresponding command is *kdesu*, not *qtsudo*).

It is what it is. Who can explain why *ls* stands for *list* or *cd* stands for *change directory*? They could have picked 10 or 20 other abbreviations or cryptic "words."

Just remember *gksudo* is for graphical applications and *sudo* is for terminal applications. For more information, read the link I posted.

---

### Post by psyne on 2007-02-01
I just remember that gk is for graphical apps like gedit and sudo is for the terminal commands like apt-get. Though I have to admit most of the time I pretty lazy about it and just type sudo though after reading some more I realize why it is a bad thing.

Here is a good thread

[http://www.ubuntuforums.org/showthread.php?t=165957](http://www.ubuntuforums.org/showthread.php?t=165957)

Sorry about the double post :)

---

### Post by tonyr1988 on 2007-02-01
sudo allows you to run a particular program as a "superuser" (or administrator) for a short period of time, to ensure security. You place it in front of a program's name to make that particular program run as a superuser (in this case, gedit, a text editor)

gksudo is simply a different type of "sudo." You use gksudo to run *graphical* programs as sudo. For example, open up a terminal. Type *nano* - this is an example of a command-line program. Notice that no other windows pop up, and you *only* use the Terminal?

Now open up a new terminal and type *gedit*. Another window pops up, and you should be able to tell the difference between a graphical program and a command-line program.

**command line programs (like nano) use sudo**
**graphical programs (like gedit) use gksudo**

I'm not sure exactly what the gk stands for...something Gnome-related, since KDE used kdesu for their graphical sudo.

---

### Post by Armor on 2007-02-01
Ah so clear now. Thanks much guys

---

