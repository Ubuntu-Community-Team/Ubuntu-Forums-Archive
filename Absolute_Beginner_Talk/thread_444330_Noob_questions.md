---
title: "Noob questions"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by sab0900 on 2007-05-15
Does the server version 6 something have a GUI?  If so what s the command to start it?  How do I get the first line in the command prompt to show up?  i can only see the 2nd or 3rd line up from the bottom (the line in which you type in) It is like you are typing blind hoping you don't mistype, only to find out after you haved typed a couple of lines.

---

### Post by SomethingCronic on 2007-05-15
I might not know quite what you mean. But if you've installed server and can't see the login prompt I would just press enter a few times so that the text will move up the screen so you can use your login name and password.

(also, to move up from the bottom and start at the top - the command 'clear' will clear the screen)

As for GUI. Server versions do not ship with a GUI installed. To install one you should:

sudo apt-get install xorg openbox

This will get you a basic window management environment (start it by typing 'startx')

If you want the full blown desktop environment type:

sudo apt-get install ubuntu-desktop

This could take some time tho.

- Mike

---

### Post by lamalex on 2007-05-15
if you're going to apt-get ubuntu-desktop you might as well just install the desktop version. A GUI on a server is just a waste of resources, dont install a gui and learn the command line! Make it a learning experiance, if you can't see your login try hitting control + alt + f2 and it should show up  in TTY2.

---

### Post by sab0900 on 2007-05-15
> **Iamalex said:**
> if you're going to apt-get ubuntu-desktop you might as well just install the desktop version. A GUI on a server is just a waste of resources, dont install a gui and learn the command line! Make it a learning experiance, if you can't see your login try hitting control + alt + f2 and it should show up  in TTY2.

Does the desktop version have the same capabilities as the server version?  I selet my hardware to have enough headroom to accomadate a gui.

---

### Post by SomethingCronic on 2007-05-16
> **sab0900 said:**
> Does the desktop version have the same capabilities as the server version?  I selet my hardware to have enough headroom to accomadate a gui.

Fundamentally server and desktop editions are the same but with different applications preloaded to suit the need (i.e server offers to install bind9, lamp - but no GUI - desktop will install GUI and office productivity apps). Everything you find on the desktop version can be installed on the server and vice versa.

If your installing the ubuntu-desktop on top of the server then you probably should have just installed ubuntu desktop as it's on the CD and would have been quicker than downloading the packages. If you just want a standard low resource windows manager for your server then I would install xorg and flux/open/black-box

- Mike

---

