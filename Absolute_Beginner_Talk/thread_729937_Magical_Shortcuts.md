---
title: "Magical Shortcuts"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by jonathanwsu on 2008-03-20
Howdy!
I just got into Ubuntu recently (7.10) and things have so far been running smoothly. Just a quick question:
I have a second NTFS partition on my drive for windows, and when I access this partition through Computer, Ubuntu places a "shortcut" to it on my desktop.  Is there any way to disable this?
Thanks

---

### Post by (((X))) on 2008-03-20
yes, disable automounting of such devices 
goto system.administration>users/groups and click on privileges tab.

---

### Post by jonathanwsu on 2008-03-20
Whoops...I don't think I was clear enough.  The "shortcut" only appears after I access the other partition.  I want to be able to use the partition in Ubuntu as well, and disabling the automounting only makes me type in my password when I want to access it.  I just don't want the desktop icon that appears after I mount the partition.

---

### Post by chalewa on 2008-04-27
yea i am having the same problem with network drives in 8.04

any ideas?

---

### Post by FragMagnet on 2008-06-07
> **jonathanwsu said:**
> Whoops...I don't think I was clear enough.  The "shortcut" only appears after I access the other partition.  I want to be able to use the partition in Ubuntu as well, and disabling the automounting only makes me type in my password when I want to access it.  I just don't want the desktop icon that appears after I mount the partition.

Either run gconf-editor or go to Applications > System tools > Configuration Editor. In the sidebar navigate to /apps/nautilus/desktop and simply untick the "volumes_visible" option. This should sort it out for you. Hope this isn't too late to help! :)

---

