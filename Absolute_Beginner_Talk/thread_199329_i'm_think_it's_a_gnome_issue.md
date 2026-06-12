---
title: "i'm think it's a gnome issue"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-06-18
i woke up one morning to find the my computer, home, and all other folders weren't on my desktop. i tried to access them from the places tab, but no luck there either. also, when i try to move things to the trash, i get an error message and it's not able to be done either. 

any ideas?

---

### Post by rowanparker on 2006-06-18
What does the error message say?

---

### Post by shanepardue on 2006-06-18
well, now i can't seem to find anything to move to trash for the error message. i went into the terminal and it shows my desktop contents are still there, but they are nowhere to be found.

i'm not able to access my home folder from one of my gdesklets and in the places tab at the top, i only have desktop (which doesnt work) and my ntfs (inaccessible also).

---

### Post by aysiu on 2006-06-18
What happens if you press Alt-F2, type ```
gnome-terminal
``` and, from there, type ```
nautilus
```?

---

### Post by shanepardue on 2006-06-18
i typed "nautilus" and this is what it showed.

"command not found"

---

### Post by aysiu on 2006-06-18
What about this? ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
nautilus
```

---

### Post by shanepardue on 2006-06-18
like always you come through! it works great now! even restarted the computer to make sure it still worked and it's looking good! i really appreciate that!

now i have two simple questions for ya...

1) what's the different between gnome and nautiilus

and 2..

2) the command you gave me..was that just reinstalling nautilus?


thanks again!!

---

### Post by uzi09 on 2006-06-18
1)
gnome = graphical interface for you to work with. you can always change it to others like: KDE, XFCE, Fluxbox, Blackbox, iceWM, and countless otheres

nautilus = it's a file explorer (recall windows explorer? yeah, similar thing)
go through all your files and stuff this way


2) yea, for some reason it wasn't installed on ur system o_O...weird
also installed the gnome desktop environment

---

### Post by aysiu on 2006-06-18
The *ubuntu-desktop* package isn't a real package. It's what's called a *metapackage*--one that points to other packages.

*ubuntu-desktop* points to all packages that make up the default Ubuntu installation (including Gnome, including Nautilus).

So the command I gave you basically just said, "Make sure at least the default programs are installed."

---

