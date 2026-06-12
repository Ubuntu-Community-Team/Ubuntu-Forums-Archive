---
title: "Installed xfce and broke command line in gnome"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by redfox on 2005-12-18
I wanted to try out the different desktop environments, so I installed xfce (xubuntu).  But when I got back to gnome, the command line was broken.  Wouldn't open from the menu.  But it works back in xfce.  Any way to fix it?

Also, is there a beginner's guide to 5.10?  The only one I can find is for 5.04.

---

### Post by kaamos on 2005-12-18
Use the menu editor to check that the menu item pointing to the terminal contains the command "gnome-terminal".

Just a thought.. Hope this helps.

---

### Post by aysiu on 2005-12-18
[QUOTE=redfox]
Also, is there a beginner's guide to 5.10?  The only one I can find is for 5.04.[/QUOTE] [http://makuchaku.info/amnesty/#](http://makuchaku.info/amnesty/#)

---

### Post by bscbrit on 2005-12-18
aysiu - you have an incredible list of useful links!

---

### Post by redfox on 2005-12-18
Here's the error message:

Details: Failed to execute child process "Terminal" (No such file or directory)

---

### Post by funkydan2 on 2005-12-18
The problem is that there is a symbolic link in /etc/alternatives that has been broken.

The command you need to run is something like
sudo update-alternatives --config x-terminal-emulator

---

