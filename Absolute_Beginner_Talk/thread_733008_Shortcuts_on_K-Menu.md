---
title: "Shortcuts on K-Menu"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-03-23
I am starting to look online for various games and other OpenGL software packages to pass the time by a bit and noticed many of them I have to compile by source. I'm slowly starting to learn how to use the ./configure, make, and make installl (although if it doesn't work perfectly beyond these three steps, I don't know what to do). I'm curious, in Kubuntu Gutsy, how does one go about adding (and naming and setting icons for) your own shortcuts to programs in the usr/bin folder?

Also, does anyone know how to take the binary scr or .tar or .tar.gz files and convert them into a .deb or .rpm package? I've found those to be much simpler and easier to install, from a user-standpoint.

---

### Post by (((X))) on 2008-03-25
Hi,

This is an interesting post, I would like to know how it works.
I do know a bit of shell, after creating some of my own script, I usually put them in /usr directory, keeps everything separated. Script I want to run as root I put in /usr/sbin directory and adjust permissions a bit, other stuff I usually put into /usr/bin

Not shure wich shortcuts you mean, 
Shell already contains paths to commands like ls and cd
If you do echo $PATH, you will see which directories are seen by shell, and contain commands available to shell.
here is how to register your command with shell:

PATH=/usr/bin/script..
but lieve all exicting directories there.

If you mean shortcuts on desktop, you could create a launcher and specify the command to run.

---

### Post by spacefreak86 on 2008-03-25
Basically in windows, its the equivalent of adding your own shortcuts to the Start Menu, or moving the location of those shortcuts from folder to folder. In Kubuntu or Ubuntu, I suppose it would be the same as moving a shortcut from the Internet category to Multimedia category, etc etc.

---

