---
title: "how to stop X from restarting after I CTRL+ALT+BKSPC?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by energy. on 2008-04-03
Can I set this so that when I press CTRL+ALT+BKSPC, instead of restarting X automatically it will just stay at the command line?

---

### Post by pseudo-random on 2008-04-03
Why would you want to do that :/

---

### Post by energy. on 2008-04-03
> **pseudo-random said:**
> Why would you want to do that :/

so that I can execute commands at the CLI without having X and gnome running.

---

### Post by MountainX on 2008-04-03
you could try xmodmap to change the key mappings of either the backspace key or a modifier key. Not sure if that fits your requirements, but it's an idea.

See man xmodmap.

You could also try to use System > Preferences > Keyboard > Layout options. There is an option for ctrl+alt+special key to be handled differently. Take a look in there and experiment.

---

### Post by pseudo-random on 2008-04-03
Like Ctrl-Alt-F1? Thats without X and gnome.

---

### Post by hessiess on 2008-04-03
ctrl+alt+f1

---

### Post by MountainX on 2008-04-03
> **energy. said:**
> so that I can execute commands at the CLI without having X and gnome running.

I suppose you know about ctrl-alt-F1, etc. 

Do you want to make your computer start up without X starting? Is that what you are asking?

---

### Post by brettg on 2008-04-03
I'm not sure why you would want to do that nor if it is even possible. 

You do know that you can ALT-F2 to a console (with X still running in bg) right?

Alternatively, if you don't want X running all the time, you can boot your machine into a lower runlevel and when you want X you can just start it from the console using the gdm command. When you logout of X you will drop back to the console again.

HTH

---

### Post by Hospadar on 2008-04-03
If you are just looking for a quick way to stop X, just do Ctrl-Alt-F1, and then "sudo /etc/init.d/gdm stop" - you could put an alias for that in your bashrc file, something like ```
alias gdmstop='sudo /etc/init.d/gdm stop'
``` so you could stop it just by typing gdmstop.

---

### Post by energy. on 2008-04-03
I didn't know about CTRL+ALT+F1. . . it does what I wanted to do

---

### Post by MountainX on 2008-04-03
> **energy. said:**
> I didn't know about CTRL+ALT+F1. . . it does what I wanted to do

Type alt-F7 to return to the desktop

---

### Post by foska on 2008-04-03
I did not know about that! That's downright dangerous! It doesn't even ask if you are sure! Under what circumstances would I need to do this?

---

### Post by ryanhaigh on 2008-04-03
> **foska said:**
> I did not know about that! That's downright dangerous! It doesn't even ask if you are sure! Under what circumstances would I need to do this?

You can disable killing X with ctrl-alt-backspace by adding the dontzap option to xorg.conf serverflags section

From man page for xorg.conf:
> 
Option "DontZap" "boolean"
    This disallows the use of the Ctrl+Alt+Backspace sequence. That sequence is normally used to terminate the Xorg server. When this option is enabled, that key sequence has no special meaning and is passed to clients. Default: off. 

---

