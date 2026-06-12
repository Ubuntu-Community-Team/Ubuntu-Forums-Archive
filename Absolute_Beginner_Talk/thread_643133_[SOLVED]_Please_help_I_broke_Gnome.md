---
title: "[SOLVED] Please help I broke Gnome"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Zoltarp on 2007-12-17
Ok here is what I did:

I was trying to move my mounted volumes off of my desktop so i followed the directions below:

"Press alt-f2 and type gconf-editor. Navigate to apps/nautilus/desktop and uncheck volumes_visible. And they disappear. But they're still mounted. Yay!"

I tried this and they did indeed disappear so I put them back as I didn't know where else to find them. Here is the problem,

 I continued to play and went to preferences and unchecked "show desktop" and of course everything on my desktop disappeared so I quickly put the check back in the box but nothing came back. I logged off and tried to log back on but gnome was hosed and wouldn't load. What can I do?

Thanks,

Bruce

---

### Post by dward526 on 2007-12-17
from the command line

sudo aptitude reinstall ubuntu-desktop

This will kill most of your custom settings, I think, but our data and applications should be safe.

---

### Post by patoruzu on 2007-12-17
> **Zoltarp said:**
> 
 I continued to play ......
Bruce

What's what you did??? Try you remember the things you changed and try undoing what you did.
It's a safe practice to comment the default lines and write your changes in the next line... so you can undo the changes easily without having to rely on your memory.

---

### Post by Zoltarp on 2007-12-17
I was following some instructions from another thread to open the configuration editor to remove mounted drives from the desktop.

 I typed alt+F2 to open the GUI then navigated to apps> nautilus> preferences> 

I was messing around in that GUI and unchecked the "show desktop" option box it predictably removed all icons from my desktop, I re-checked the box and nothing re-appeared. I exited the Coniguration editor and logged off.

When I tried to log back on gnome failed to load just showed me a background never loaded to desktop.

---

### Post by Zoltarp on 2007-12-17
Now that I have reinstalled Ubuntu-desktop "Gnome"  from the command prompt I now have no GUI previously I was able to use KDE to logon to Ubuntu as I had installed the KDE desktop. Now what I get when I restart is the command prompt. Please help this is the most costly check box click I have ever made.

---

### Post by Zoltarp on 2007-12-17
Nevermind I got it working with typing sudo gdm at the command line. This loaded kde, i logged off and selected a gnome session and that brought up gnome and my desktop, everything is now right in the world.

Thanks Dward526

---

