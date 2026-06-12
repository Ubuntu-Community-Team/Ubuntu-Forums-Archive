---
title: "ctrl-alt-F1, startx doesn't work"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by KnavishClout on 2008-03-13
Ok so n00b running gOS and on a quest to better install my NVIDIA drivers I ended up typing

ctrl-alt-F1

I can't figure out how to get back to the pretty graphical user interface.  I've tried ctrl-alt-F7, but all I get is a blank screen.  I've tried "startx", but all I get is a lengthy error message.  Any advice for a total n00b?

---

### Post by Oldsoldier2003 on 2008-03-13
> **KnavishClout said:**
> Ok so n00b running gOS and on a quest to better install my NVIDIA drivers I ended up typing

ctrl-alt-F1

I can't figure out how to get back to the pretty graphical user interface.  I've tried ctrl-alt-F7, but all I get is a blank screen.  I've tried "startx", but all I get is a lengthy error message.  Any advice for a total n00b?

CTRL+ALT + F9

---

### Post by KnavishClout on 2008-03-14
I tried you advice, but unfortunately I got no response (at all) from my PC.  Any other ideas?

---

### Post by aeiah on 2008-03-14
sudo /etc/init.d/gdm restart

(this restarts gnome desktop manager)

---

### Post by tad1073 on 2008-03-14
ctrl+alt+F7 starts x

---

### Post by The Titan on 2008-03-14
if all else fails just hard restart your computer.

---

### Post by aeiah on 2008-03-14
there's also 

sudo reboot now

of course

---

### Post by bumanie on 2008-03-14
crtl-alt-F1 stops xserver the usual combination to restart xserver is 
ctrl-alt-F7

---

### Post by KnavishClout on 2008-03-14
I haven't tried "sudo /etc/init.d/gdm restart" yet, I'll try that in a few moments.

ctrl+alt+F7 just gives me a blank screen

Restarting my computer just brings me back to the prompt screen (the one I was in after hitting ctrl + alt + F1)

---

### Post by KnavishClout on 2008-03-14
Ok "sudo /etc/init.d/gdm restart" looked like it was going to do the trick, but now my monitor is displaying the "out of range" message.

---

### Post by joshrobinson on 2008-03-14
sounds like your resolution is wrong

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
try that, and set your resolution

---

