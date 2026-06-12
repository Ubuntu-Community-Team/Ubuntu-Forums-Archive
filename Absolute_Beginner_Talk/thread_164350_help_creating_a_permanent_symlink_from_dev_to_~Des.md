---
title: "help creating a permanent symlink from /dev to ~/Desktop"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Lord_Drakkus on 2006-04-22
I'm trying to make a symlink from one of my Windows partitions (My Documents) to a folder in ~/Desktop, and I'm having trouble making it permanent.

Running "mount --bind '/dev/win.progs/My Documents' ~/Desktop/My.windocs" works temporarily, but every time I reboot I have to set the symlink again...

So here's my problem, I don't know either: A) which file to put that line into to set the symlink automagickally, or B) if there's a better way to do it.  I've checked out the udev man pages and that just doesn't seem to be the right way to do it...

Lord Drakkus (of Corinthia...  ;) )

---

### Post by aysiu on 2006-04-22
First, make your Windows mounting permanent:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Then, navigate to My Documents and...

if you're using Gnome, middle-click-drag the My Documents folder to the desktop and select "link here."

if you're using KDE, just drag it to the desktop (left-click) and select "link here."

---

### Post by Lord_Drakkus on 2006-04-22
I KNEW there had to be a simpler way to do it... Thanks aysiu.

Now, just for the fun of it, to find a way to do basically the same thing with the command line...  :D

---

### Post by aysiu on 2006-04-22
```
ln -s "/windows/My Documents" "~/Desktop/My Documents"
``` probably would work.

---

