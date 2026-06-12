---
title: "install real player"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by gmcm1979 on 2006-08-25
can anyone help me install real player i have downloaded the .bin file

---

### Post by Crosbie on 2006-08-25
Did you try this (from their site):

Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

---

### Post by Jukey on 2006-08-25
Don't forget to navigate to the right directory

---

### Post by gmcm1979 on 2006-08-25
ried it got following error

graham@graham-desktop:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
graham@graham-desktop:~$

---

### Post by Jukey on 2006-08-25
what directory is the .bin flie in?

---

### Post by gmcm1979 on 2006-08-25
it is on desktop. where should it be

---

### Post by Jukey on 2006-08-25
that's fine, I'm just not sure the context to get the terminal pointing to the desktop.

EDIT:
[http://monkeyblog.org/ubuntu/installing/#navigating_the_terminal](http://monkeyblog.org/ubuntu/installing/#navigating_the_terminal)

try that if you don't already know much about the terminal

---

### Post by Crosbie on 2006-08-25
A terminal starts in your /home, so try:

cd Desktop

before running your install commands. :)

---

