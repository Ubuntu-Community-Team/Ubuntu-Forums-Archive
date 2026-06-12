---
title: "Launchers"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Cirrocco on 2007-06-26
Ok, I know how to make one, I know how to edit it's properties.

but:
- what are launchers exactly?  are they the equivalent of a Mac Alias?
- is it possible to edit them in a text editor (or anything else)?
- are they a linux thing or a Ubuntu-specific thing?
- are they cross platform? (could I copy one to another OS like Fedora or Slax and have it work)

/thanks,

---

### Post by greg_g on 2007-06-26
> - what are launchers exactly? are they the equivalent of a Mac Alias?
Launchers are just a clickable way of running a command.  And I'm not really sure what a Mac Alias is, but think like a windows "shortcut"

> - is it possible to edit them in a text editor (or anything else)?
This is all I could find on my computer: /home/greg/.gnome2/panel2.d/default/launchers
I only have one there, out of my 13 launchers, so more help is needed on that one.  (see my post below)

> - are they a linux thing or a Ubuntu-specific thing
They are a gnome thing.

> - are they cross platform? (could I copy one to another OS like Fedora or Slax and have it work)
And since they are a gnome thing, as long as you move your gnome configuration over (the .gnome2 in your home dir) it should work.

Hope that helps, and if anyone else can fill in the holes that would be great,

greg

---

### Post by Nekiruhs on 2007-06-26
> **greg_g said:**
> Launchers are just a clickable way of running a command.  And I'm not really sure what a Mac Alias is, but think like a windows "shortcut"


This is all I could find on my computer: /home/greg/.gnome2/panel2.d/default/launchers
I only have one there, out of my 13 launchers, so more help is needed on that one.


They are a gnome thing.


And since they are a gnome thing, as long as you move your gnome configuration over (the .gnome2 in your home dir) it should work.

Hope that helps, and if anyone else can fill in the holes that would be great,

greg
Launchers are also found in KDE, but there called links to applications. Its just a shortcut, with some extra info. They usually have the extension .desktop.

---

### Post by greg_g on 2007-06-26
Ok, I found where most of them are:

/home/greg/.gconf/apps/panel/objects/

and the the different object_number directories have XML files.

Hope that helps.

greg

---

### Post by Cirrocco on 2007-06-27
hey!  that's pretty cool!

Thanks,

---

