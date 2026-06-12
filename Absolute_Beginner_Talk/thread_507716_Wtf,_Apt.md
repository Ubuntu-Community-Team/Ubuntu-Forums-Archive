---
title: "Wtf, Apt?"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Southeast First on 2007-07-23
So recently I just noticed when I install a program through APT it doesn't add an item on my programs menu anymore. What the hell, now I have to go in and do it myself every time which is a big deal because I'm nitpicky and have to search out for a pixmap for the damned program.

Is this a common problem? Is there a fix?

---

### Post by asmoore82 on 2007-07-23
have you tried logging out and back in and seeing if the program shows up in the menu then?

---

### Post by KIAaze on 2007-07-23
It's up to the package creators to add the shortcuts.
If they don't do it, you have to do it manually.
It's the same in Windows.

For what programs did it happen in your case?

---

### Post by Southeast First on 2007-07-23
> **asmoore82 said:**
> have you tried logging out and back in and seeing if the program shows up in the menu then?
I tried both with Gnome and XGL.
> **KIAaze said:**
> It's up to the package creators to add the shortcuts.
If they don't do it, you have to do it manually.
It's the same in Windows.

For what programs did it happen in your case?

I guess that makes since, it's just done it non-stop today with Nicotine, Superkaramba, Azureus (after I reinstalled).

---

### Post by KIAaze on 2007-07-23
Well, then it's not normal, because those packages seem to have shortcuts (*.desktop files) in them. :/

Do you have the following files?:
> /usr/share/applications/azureus.desktop
/usr/share/applications/nicotine.desktop
/usr/share/applnk/Utilities/superkaramba.desktop

Superkaramba seems to be created for KDE, so maybe it's normal that it doesn't create a shortcut in Gnome.
The other two should work in Gnome.

---

### Post by #Reistlehr- on 2007-07-23
try this command after you run apt:


killall gnome-panel

---

### Post by Southeast First on 2007-07-23
I just installed Frostwire through Automatix2 and it added an item for Frostwire on my menu, so now I'm not sure what's going on.

---

