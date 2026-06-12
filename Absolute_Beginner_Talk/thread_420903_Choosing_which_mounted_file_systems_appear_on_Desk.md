---
title: "Choosing which mounted file systems appear on Desktop"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-24
I'm having trouble finding a good tutorial which will help me to choose which mounted file systems appear on the desktop. 

One of the major things that I'm having trouble with is putting my "Filesystem" icon on the Desktop. All the tutorials that I have read are unclear on this. The windows partition is automatic which is ok for now, i'm deciding  if it should be hidden or not.

Also, I don't like when cd's show up on the Desktop; I would rather access it from Places->Computer. Is there a way to disable cd's from showing up on the Desktop automatically?

---

### Post by LaurelLynn on 2007-04-24
Dear noorez,

Actually it is really easy.  Just go to the top panel and click on Places.  You can then click on the entry for say Computer, holding done the left mouse button while you drag it and drop it on the desktop.

For Filesystem open up Computer and drag the icon in the right pane not the left.

---

### Post by noorez on 2007-04-24
OK...that appears to be working, however, a small lock icon was attached to the icon when I dragged it to the desktop? Why is there a lock on the Filesystem one, and no lock on the icon for the windows partition which was automatically mounted? If I right click on properties on Filesystem, it shows that I am the owner, but for the windows partition it shows root as the owner but with no lock icon. What does this lock icon mean?

---

### Post by LaurelLynn on 2007-04-24
Probably because you own the link and Filesystem is an alias for /  which is owned by root.  So you only have read access to that folder.  You should still be able to browse to and change any files that you own.

To open it up as root you have to create a custom launcher. Right click on the desktop and select ¨Create Launcher...¨ For name put ¨Filesystem¨ for command ¨gksu nautilus /¨.  Then hit the Icon button to select one. Finally hit OK.

Double clicking on the icon should open / with root access.

---

