---
title: "Saving preferences?"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-09
I am running live, but is there anyway I can save my preferences so when I install Ubuntu for final, I don't have to reset all my cookies and window positioning?

---

### Post by mlind on 2006-04-09
I'm not sure, but if you do have directories

```

~/.gnome
~/.gnome2
~/.nautilus
~/.mozilla

```

then make a backup of those. Even better, make a backup of your whole $HOME
directory and after installing (persistent) Ubuntu, overwrite files on your home
directory with the ones you backed up.

The best way to achieve this is using tar -archiver imo.

---

### Post by dylonium on 2006-04-09
Sounds good to me!

---

### Post by dylonium on 2006-04-09
Wait, where is there a home directory? It has to be a folder under the cdrom I'm running off. Please help me!

---

### Post by mlind on 2006-04-09
[QUOTE=dylonium]Wait, where is there a home directory? It has to be a folder under the cdrom I'm running off. Please help me![/QUOTE]

I'm not sure, I've never tried liveCD actually. 

does /home directory exist? 
what's the output of command *df*
does *echo $HOME* show location of home directory?

---

### Post by dylonium on 2006-04-09
[QUOTE=mlind]
does /home directory exist? 
what's the output of command *df*
does *echo $HOME* show location of home directory?[/QUOTE]

it does not exist unless it's hidden. how can i output a command of *df* and what deos that mean? where would i *echo $HOME*? the terminal?

---

### Post by mlind on 2006-04-09
[QUOTE=dylonium]it does not exist unless it's hidden. how can i output a command of *df* and what deos that mean? where would i *echo $HOME*? the terminal?[/QUOTE]

yeah, open a terminal window and write commands there.

---

