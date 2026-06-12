---
title: "no GNOME only KDE works???"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-06-24
I can not get my Gnome interface to work at all..........all I get is a blue screen with two white bars both top and bottom......NOTHING ELSE.......I have to cntr alt backspace to get out of it.  But my KDE and Xinterface work fine?

Noah

---

### Post by Happy_Man on 2007-06-24
Aren't we already discussing this nine threads down? :confused:

---

### Post by nynoah on 2007-06-24
actually the original problem with the screen resolution is fixed.....I just started another thread for a different problem.  I hope I did not offend.  I just wanted to spell out my current problem more concisely on the name of the thread.

Noah

---

### Post by nynoah on 2007-06-24
No ideas............I know this is a weird problem.......I just don't want to loose my whole computer.   I can go into KDE and Xserver 

I can not even go into fail safe Gnome...........its a blue screen too.  Is there something deal with the grafix that would only effect Gnome and not KDE?

---

### Post by cogadh on 2007-06-24
How did you install Gnome (i.e. what command did you use, what packages did you install, etc.)?

---

### Post by nynoah on 2007-06-24
Well when I am talking about Gnome......just to clarify...........I am referring to Ubuntu.

I installed originally fiesty in the X64.  I use to run Edgy in i86 before this......so I am not totally new to Ubuntu.....but I always run into these really weird problems...............Is there any way to reinstall the Gnome part without losing everything?

---

### Post by cogadh on 2007-06-24
So you didn't install Gnome on top of a Kubuntu install? In that case, you might try booting your system, do a CTRL-ALT-F1 to get down to the console, log back in and run:
```
sudo apt-get --reinstall install ubuntu-desktop
```
That will reinstall the whole GUI and may get it working again.

If you did install Gnome over Kubuntu, doing this will remove your Kubuntu boot screen and the KDM login and replace them with the Ubuntu boot screen and the GDM login.

---

### Post by alienexplorers on 2007-06-24
Have you tried this:

> [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

---

### Post by nynoah on 2007-06-24
I don't want to remove KDE.....

Cogadh.........if I do this........will I lose any of my files?  I don't want to loose all my music and pictures to a hard drive wipe.

Noah

---

### Post by cogadh on 2007-06-24
No, you won't lose anything, it doesn't wipe the drive, it just re-installs all of the Gnome GUI applications and dependencies.

---

### Post by nynoah on 2007-06-24
OK let me try

sorry to sound dumb.  I was just making sure.....safer rather than sorry you know

---

### Post by nynoah on 2007-06-25
Nope didn't work..............When it goes to Gnome it gives me the loading screen fine.  When it finally hits the home screen it is light blue with white bars top and bottom......nothing else.

??

Noah

---

### Post by swoll1980 on 2007-06-25
Kde is better anyways your not missin' nothing

---

### Post by nynoah on 2007-06-25
I like KDE too....but it worries me......I lost my last ububtu system to a crash.....I don't want to lose this one too.

---

