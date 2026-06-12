---
title: "Saving Nvidia settings crashes window manager.."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Colorado_baja on 2007-05-13
Every time I try to save my Nvidia settings useing the save to x config button, I lose the border around my windows, so I cant move, expand or close them.. 
Im trying to run twin view with two 17" LCD's.. I have reloaded the system a couple times with the same result. 
I used Envy to install the Nvidia drivers..
Thanks in advance to anyone who can point me in the right direction..

Greg

---

### Post by Tux Aubrey on 2007-05-14
I've had several problems with nvidia-settings (but not the particular ones you mention).  I know that part of the problem is that the "save" function requires admin priviliges (to write the changes to xorg.conf).  That means you either need to change the launcher to run it with gksudo or launch it from terminal with the sudo command.  I can't give you the full command because I'm on a windows machine right now (its probably just "sudo nvidia-settings").  If you can't work it out, respond to this to bump the thread back to the top and someone (possibly me if I'm home by then) will come to your assistance.

---

