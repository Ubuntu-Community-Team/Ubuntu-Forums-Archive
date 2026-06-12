---
title: "Where's GUI?"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by tiggertiffin87 on 2005-11-25
I installed Ubuntu and when I'd start my computer and select it, it'd automatically go to my Gnome login screen.  I recently installed some packages and now it just goes to the command line.  A fellow poster let me know that startx gets me into Gnome but how do I get it to automatically go there like before?  BTW when I go to System and Log Out, it just logs out of the GUI and goes to the command prompt again.  I can't figure out how to shut down other than the power button.

---

### Post by ubuntufella on 2005-11-25
Well I am new to linux as well but I think that if you type into the command line the following:

```
sudo shutdown -P -t now
``` at the command line the computer will shut down. Try it and see.

As for fixing the problem, I wouldn't know. Sorry.

---

### Post by Merkaba on 2005-11-25
A simpler way of shutting down from the command prompt would be to type the command
```
sudo halt
```
As for the problem, open a terminal from within Gnome and type that command in - that'll shut the machine down, then when you restart it it might boot into Gnome again - not a really technical answer, but I've had this problem before (using a previous version of Ubuntu) and this fixed it for me -not sure how or why, but it worked for me somehow...

---

### Post by towsonu2003 on 2005-11-25
here is another newbie reply :)

When in gnome, go to System>Administration>Services and make sure "Graphical login manager" (gdm) is checked... Don't know how to do that in command line in ubuntu/debian...

---

### Post by tiggertiffin87 on 2005-11-25
Yup, it's checked.

---

### Post by RaymondQE on 2005-11-25
Try reading this link:
[http://www.ubuntuforums.org/showthread.php?t=88783&highlight=system+runlevels](http://www.ubuntuforums.org/showthread.php?t=88783&highlight=system+runlevels)

Hope that helps.

RaymondQE

---

### Post by Kyral on 2005-11-25
try

```
sudo dpkg-reconfigure gdm
``` and see if that works

---

### Post by tiggertiffin87 on 2005-11-26
[FONT="Arial Narrow"][COLOR="Magenta"]:KS :KS :KS :KS
Thank you so much.  I had the same problem as that guy in that thread did.  Thanks![/COLOR][/FONT]


[QUOTE=RaymondQE]Try reading this link:
[http://www.ubuntuforums.org/showthread.php?t=88783&highlight=system+runlevels](http://www.ubuntuforums.org/showthread.php?t=88783&highlight=system+runlevels)

Hope that helps.

RaymondQE[/QUOTE]

---

