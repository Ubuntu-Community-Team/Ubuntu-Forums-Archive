---
title: "[SOLVED] menu bars"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by myst1c on 2008-01-20
my menu bar and task bar disappeared for no apparant reason... can anybody tell me how to get them back?

---

### Post by cecure on 2008-01-20
were they there before?  if so what happened before they disappeared?

---

### Post by CupofDice on 2008-01-20
Try Alt+F2, then type killall gnome-panel. If they don't show up, type Alt+F2 again, then type gnome-panel.

---

### Post by myst1c on 2008-01-20
alt+F2 doesn't work for me... i believe it's a hardy issue, although it worked fine in hardy at first... i can still navigate through all my files due to a home folder shortcut on my desktop... is there a way i could get to terminal or other programs through there?

---

### Post by cecure on 2008-01-20
You can get to a terminal with ALt-F2 and the click on 'show list of known programs' scroll down and see if its there.

---

### Post by banewman on 2008-01-20
You can browse from your home folder to /usr/bin and double click on gnome-terminal and it should open
:)

---

### Post by myst1c on 2008-01-20
i tricked my terminal into opening... first it told me it wasn't installed...  

```
myst1c@Candy:~$ killall gnome-panel
gnome-panel: no process killed
myst1c@Candy:~$ gnome-panel
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found
myst1c@Candy:~$ sudo apt-get install gnome-panel

```

turns out there's a problem with timidity, as shown here:

```
Errors were encountered while processing:
 timidity
 timidity-interfaces-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i had the idea that i could fix it if i went to my synaptic package manager, and mark timidity for reinstallation... but it won't let me and tells me this...

> You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them.

anybody have any ideas?

---

### Post by CupofDice on 2008-01-20
sudo apt-get remove --purge timidity gnome-panel , then reinstall gnome-panel. If that doesn't work, all I can think of is restarting (have you done that yet?).

You might want to wait for someone more knowledgeable than me.

---

### Post by myst1c on 2008-01-20
UPDATE: I have fixed the problem. I went into synaptic and used the thing to make a file that downloads the stuff via terminal, and i set it to update timidity... after it was updated, i typed gnome-panel into terminal and now all is good... thanks guys

---

### Post by st33med on 2008-01-20
Good. Make sure to mark this as solved! (I must sound like one of those 'Safety First!' people :P)

---

