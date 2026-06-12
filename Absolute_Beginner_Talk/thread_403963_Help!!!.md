---
title: "Help!!!"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-07
ok.  i just bought a wacom tablet and followed some directions off this site to get it up and running.  the only problem is that once i restarted x so i could test out my changes to xorg.conf, it gave me the ubuntu version of the blue screen of death saying it couldn't start x.  could anyone tell me how to fix this?!?  i REALLY want my ubuntu partition back up and running.  i'm using windows right now to write this post.  -barfs-

---

### Post by Famicommie on 2007-04-07
Use ctrl+alt+F1 to switch to a console. Log in, and restore xorg.conf from backup or manually with nano.

---

### Post by locke.dragon on 2007-04-07
how do i restore it with nano?  i'm new to linux and don't know what that is.  :P

---

### Post by overdrank on 2007-04-07
> **locke.dragon said:**
> how do i restore it with nano?  i'm new to linux and don't know what that is.  :P

This thread looks like a good start
[http://ubuntuforums.org/showthread.php?t=25151](http://ubuntuforums.org/showthread.php?t=25151)
hope it helps!:)

---

### Post by ComplexNumber on 2007-04-07
further to what Famicommie has suggested, what you could do is to restore the old xorg.conf. you will noticed that, when you go to /etc/X11, you may see something like in the screenshot. i've highlighted in red the original xorg.conf file thats has a tilde(~) after it. whenever you change a file, a backup is automatically created from the last change and has a tilde appended to it to indicate that its a backup. to restore the backup, type the following on the commandline:
**sudo mv xorg.conf~ xorg.conf**

---

### Post by Famicommie on 2007-04-07
> **locke.dragon said:**
> how do i restore it with nano?  i'm new to linux and don't know what that is.  :P

Getting yourself into deep trouble is the best approach to really learning linux. :D

Hopefully, before you edited your xorg.conf file, you made a back up.

Do you remember typing something like
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
before you edited it? It doesn't necessarily have to be .bak as some people like to use .backup. If you did, then all you'll have to do is type
```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
Which will overwrite xorg.conf with the original from before you modified.

Otherwise, you will have to enter the command:
```
sudo nano /etc/X11/xorg.conf
```
and revert the changes that you made from the text editor nano.

---

### Post by locke.dragon on 2007-04-07
the only problem is that i can't get to the graphical interface.  i guess i could to this from the text only version.  :P  i didn't make a backup THIS time, but i think i have an old backup from when it was still working.  i'm such an IDIOT!  lol.  out of curiosity, is there a way to EDIT xorg.conf from the text only black and white NON-gdm style of ubuntu which i'm now stuck in?  and that's the tutorial i followed when i fried xorg.conf.  :P

---

### Post by ComplexNumber on 2007-04-07
> **locke.dragon said:**
> the only problem is that i can't get to the graphical interface.  i guess i could to this from the text only version.  :P  i didn't make a backup THIS time, but i think i have an old backup from when it was still working.  i'm such an IDIOT!  lol.  out of curiosity, is there a way to EDIT xorg.conf from the text only black and white NON-gdm style of ubuntu which i'm now stuck in?
use nano to edit the file and/or restore the backup. just type in 'nano xorg.conf' when you are in the /etc/X11 directory.

nano is a commandline editor. its not graphical.

---

### Post by locke.dragon on 2007-04-07
ok.  FIXED IT!!!  thanks a billion guys.  the only problem is that now i can't get to wacom-tools.  the tut says to enable it in the applications menu, but i can't find that.

---

### Post by ComplexNumber on 2007-04-07
> **locke.dragon said:**
> ok.  FIXED IT!!!  thanks a billion guys.  the only problem is that now i can't get to wacom-tools.  the tut says to enable it in the applications menu, but i can't find that.
are you saying that the menu entry for wacom-tools is not visible in the menu? if so, right click on the main menu, then select 'edit menu'. have a look through the menu to see if the entry is there and if it has a tick on the  left  hand side of the entry. it may well be that it is unticked (ie is not visible).

---

### Post by locke.dragon on 2007-04-07
i looked. it's not there.  all i have it 'touchpad' for my symantec laptop touchpad.

---

