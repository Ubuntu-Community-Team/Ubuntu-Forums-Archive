---
title: "File permissions"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Sidney_the_n00b on 2006-08-22
I'm trying to get my wireless card to work, and I've found a few guides here on this forum (which have been helpful) but the [one I'm currently looking at](http://www.ubuntuforums.org/showthread.php?t=201633&highlight=wg311v2) requires me to change a system file. Unfortunatly the user I am using doesn't have permission to change it, and I can't figure out how to get permission. I've tried logging in under the username "Root" with the only password I put in while loading the os, but that doesn't seem to work.

Sorry about the stupid question, but could someone please tell me how to get permission to change said file?

---

### Post by TheMono on 2006-08-22
Assuming you are using the terminal, put the term "sudo" in front of any command, ie, sudo apt-get etc, and the command will be executed as root.

If you're doing a command that launches a graphical interface, ie, gedit or somesuch, you can use gksudo instead, which is the same thing with graphics.

Oh, and if you are wanting a file browser run as root, where you can move around files, etc, graphically, use "gksudo nautilus"

---

### Post by RRS on 2006-08-22
Add sudo to the beginning of your edit command. Example; "sudo gedit /systemfile".

At the prompt enter the password you created when installing. It won't show on the screen, just type it in and hit enter.

---

### Post by Druidor on 2006-08-23
Being new to linux myself, the command line currently eludes my prowess level, fortunatly I found out about the following command

```

gksudo nautilus

```

This has made it possible for me to do all of the things I want to do as root via the GUI even edit files & then drag & drop to replace the originals.

Hope it helps, but I expect you are further along the linux road than I. :p

---

