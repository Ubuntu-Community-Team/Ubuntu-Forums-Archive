---
title: "Shortcut on desktop"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by DerMika on 2005-07-18
I managed to install Ubuntu and I automounted my NTFS C and D drives (read-only of course) from windows. But now I want a shortcut on my GNOME desktop to  a directory on my C-share (c:\documents and settings\user\my documents\). By the way, c is mounted as /media/windows_c.

is this possible? I found something called symlink but i don't seem to get it working

---

### Post by JayCnrs on 2005-07-18
You will want to right click on your desktop then choose Create Launcher. Then give the shortcut a name and on the command line you will want to put:

**nautilus /media/windows_c/"documents and settings"/user/"my documents"** 

Make sure you put in the quotes or it won't work.

HTH

Let us know if it works.   ;-)

---

### Post by brim4brim on 2005-07-18
[QUOTE=JayCnrs]You will want to right click on your desktop then choose Create Launcher. Then give the shortcut a name and on the command line you will want to put:

**nautilus /media/windows_c/"documents and settings"/user/"my documents"** 

Make sure you put in the quotes or it won't work.

HTH

Let us know if it works.   ;-)[/QUOTE]
 It maybe case sensitive for the location e.g. My Documents instead of my documents.

---

### Post by aysiu on 2005-07-18
Or if you navigate to the folder within Nautilus, middle-click the folder and drag it to the desktop. Select "link here."

---

### Post by Nequeo on 2005-07-18
[EDIT] Someone else beat me to it![/EDIT]

You can also drag the folder you want to make a short cut with onto the desktop using the **middle mouse button**. When you let go of the button you'll see the option to 'link here'. 

Someone else on this forum taught me that trick... and I've found it useful ever since :)

It's worth noting that this actually creates a directory in your desktop folder that links to your Windows folder, as opposed to creating a launcher that starts nautilus at the right place. I can't say if that's better or worse... Just different.

---

### Post by DerMika on 2005-07-19
[QUOTE=Nequeo][EDIT] Someone else beat me to it![/EDIT]

You can also drag the folder you want to make a short cut with onto the desktop using the **middle mouse button**. When you let go of the button you'll see the option to 'link here'. 

Someone else on this forum taught me that trick... and I've found it useful ever since :)

It's worth noting that this actually creates a directory in your desktop folder that links to your Windows folder, as opposed to creating a launcher that starts nautilus at the right place. I can't say if that's better or worse... Just different.[/QUOTE]
 I'll try all your options tonight when i'm home :)

I want to know as many as possible ways of doing this ;)

---

