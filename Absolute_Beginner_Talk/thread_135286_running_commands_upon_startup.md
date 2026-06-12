---
title: "running commands upon startup?"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by furtivefelon on 2006-02-23
hello, i want to run the command: xmodmap ~/xmodmap.command during start up (it contains the commands needed to switch control and Caps Lock).. However, it doesn't work after i tried to put it in session manager (with an order of 50), it is in the list of running programs, but it doesn't have the effect i wanted (switch keys), i have to invoke it manually if i want to switch the keys. So the question remains how do you invoke a specific command upon startup?

---

### Post by aysiu on 2006-02-23
[When I wanted a complex command to be a simple command, a kind soul here on the forums taught me how to write a script for it.](http://www.ubuntuforums.org/showthread.php?t=89638) You could do it by doing something like this: ```
sudo gedit /usr/local/bin/modmapit.sh
``` and then put this in the empty document: ```
#!/bin/sh
xmodmap ~/xmodmap.command
``` Save the file and then ```
chmod +x /usr/local/bin/modmapit.sh
``` to make it executable and then add the command ```
modmapit.sh
``` to the list of startup programs. In Gnome, this is System > Preferences > Sessions > Startup Programs. I can't remember off the top of my head where it is in KDE.

---

### Post by Eltern on 2006-03-02
Hello, I'm trying to do the exact same thing as furtivefelon, but I'm using KDE. Any ideas on how to do this? I'm a complete command line novice, so some explanation may be necessary. I do understand, however, that the gedit command aysiu provided shouldn't work for me, because it's Gnome-dependent, correct?

Thanks!

---

