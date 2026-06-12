---
title: "Total pneub, need help getting GUI"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by wmcheesemaster on 2006-01-15
Alright, I managed to install Ubuntu on my old laptop without too much trouble or blood loss, now i'm just trying to figure out how to get the actual graphical interface thingy running.

I turn it on, it loads a whole bunch of stuff, and i'm left looking at the command line screen. Tells me to login, so i enter "root" and my password. Seems to work, so now its telling me 
"   root@laptop1:~#.  "

Now i'd like to know where to go from here to get an actual graphic type thing running, because all this black and white text is freaking me out.

Also, once i get this running is it possible to skip all the text based stuff so it loads right into the GUI?

A final note, i'm running it right now on a Toshiba 310CDS laptop. I doubt it's gonna run very fast, i'm just hoping to learn a bit about linux before seeing if i can't switch to damn small linux or something faster.

Thanks for the help:smile:

---

### Post by hen3rz on 2006-01-15
Hello,

I'm guessing you chose to do a "server" install when u installed ubuntu which is completley text based with no gui. To install the gui when you are in a server install, log in as root and type in the following:
```
sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal synaptic
```

That will give u a basic gui with nothing else installed.

---

