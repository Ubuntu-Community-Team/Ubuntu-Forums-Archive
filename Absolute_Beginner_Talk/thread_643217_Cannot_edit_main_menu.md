---
title: "Cannot edit main menu"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by mikebeecham on 2007-12-17
For some reason I am having real issue with my menu panel today.  For some reason I have lost my Applications section from the menu panel, when I was attempting to access Main Menu from system preferences.

Now, despite being able to click on the link for Main menu, all I get is "Starting Main menu" on the panel, which then disappears.

I have tried the sudo debconf gnome-panel command which brings everything back until I reboot...then I lose it again.

can anyone help?

---

### Post by philinux on 2007-12-17
```
sudo apt-get --reinstall ubuntu-desktop
``` should sort it.

---

### Post by mikebeecham on 2007-12-17
I'm getting an invalid operation with that?

"E: Invalid operation ubuntu-desktop"

---

### Post by philinux on 2007-12-17
you did use 

sudo   ?

---

### Post by rsambuca on 2007-12-17
Isn't that a little excessive to just fix the gnome-panel?  Why not just re-install the gnome-panel first and see if that works.

---

### Post by mikebeecham on 2007-12-17
How do I do that?

---

### Post by philinux on 2007-12-17
> **rsambuca said:**
> Isn't that a little excessive to just fix the gnome-panel?  Why not just re-install the gnome-panel first and see if that works.

Yep my bad I meant panel, got carried away there.

sudo apt-get --reinstall gnome-panel

---

### Post by mikebeecham on 2007-12-17
Invalid operation on that one as well.

---

### Post by philinux on 2007-12-17
Go to synaptic

system>admin>synaptic

search gnome-panel

Mark it for reinstallation.

---

### Post by rsambuca on 2007-12-17
I think the correct code would actually be```
sudo apt-get install --reinstall gnome-desktop
```

---

### Post by mikebeecham on 2007-12-17
HI...that has gone a little way to solving some of my issues this evening.  Linux no longer crashes or hangs when I try to 'quit', but I still dont have anything under the 'Applications' section of my menu bar, except a small white square.

I have also tried to access main menu, to see if I could edit it and 'restore' my applications, but it still do not open.

Any other thoughts?

---

### Post by mikebeecham on 2007-12-17
Furthermore, I just noticed that when I create a new user, the menus are there just fine.  Therefore (with my limited knowledge) I can tell it's to do with this login.

I did find a post on a related topic where the 'victim' was being asked to copy over the .gconf, .gconfd, .gnome and .gnome2 folders over from the working login to the not-working login.

I have tried this, and it made no difference, other than all my desktop settings for the panels, icons etc had disappeared.

---

