---
title: "cannot find disks under systems-admination"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by joramdam on 2007-04-07
The icon for disks are not there. 

   Check disk space usage and view the partition table
1. Open System &#8594; Administration &#8594; Disks .
2. Select the Harddrive, then the Partitions tab
3. Each partition will be listed under Partition List, with disk space and mount point.

---

### Post by ComplexNumber on 2007-04-07
i'm not entirely sure what you mean :). 

are you looking for a program called gparted? if so, its under main menu -> system -> administration -> gnome partition editor.

---

### Post by joramdam on 2007-04-07
> **ComplexNumber said:**
> i'm not entirely sure what you mean :). 

are you looking for a program called gparted? if so, its under main menu -> system -> administration -> gnome partition editor.

Yes, cant find gnome partition editor.

Bye the way i am using feisty

---

### Post by joramdam on 2007-04-07
Sorry stupid question gparted was not installed:)

---

### Post by ComplexNumber on 2007-04-07
> **joramdam said:**
> Yes, cant find gnome partition editor.

Bye the way i am using feisty
oh, i see. i haven't used feisty yet, so i don't know what the changes are to the menu.

btw can you see system-tools category in the menu? in edgy, the menu has the following entries: accessories, games, graphics, internet, other programming, sound & video, system tools.
however, the system tools entry isn't visible by default, it needs to be made visible. in case you don't know and it isn't visible by default, right click on the main menu and select the menu editor.
i was thinking that its maybe in system tools.


EDIT: ok. well thats solves that then :D

---

### Post by joramdam on 2007-04-07
And now i cant resize the partiton, why ?

---

### Post by UpperNinety89 on 2007-04-07
> **joramdam said:**
> And now i cant resize the partiton, why ?

It could be one of many reasons, we'll need a bit more information.

---

### Post by joramdam on 2007-04-07
Ext3 boot partion is the one i want to resize.....

---

### Post by ComplexNumber on 2007-04-07
as UpperNinety89 says, we need slightly more info. 
what happens when you try to resize the partiton?

---

### Post by joramdam on 2007-04-07
Well, when i start the GUI Gparted the options resize are grayed out. Cant resize from the GUI. Dont know how to explain it better. But all the options are grayed out ?

---

### Post by joramdam on 2007-04-07
But maby its impossible sinse i used the whole drive when i installed ?

---

### Post by freebeer on 2007-04-07
off the top of my head... you probably have to unmount the drive first.  It's not good practice to resize a mounted drive.  (assuming it were even possible)  :D

---

### Post by ComplexNumber on 2007-04-07
> **joramdam said:**
> Well, when i start the GUI Gparted the options resize are grayed out. Cant resize from the GUI. Dont know how to explain it better. But all the options are grayed out ?
probably because you can't resize a partition whilst its still mounted. you MUST unmount a partition before attempting to change it in any way.

btw for future reference, never unmount root or home partition whilst you are still using it :D. just in case you need to in future. the way to get around that is to use a live CD.

EDIT: oops. looks like someone got there befor me.

---

### Post by joramdam on 2007-04-07
Ok, thanks for quck replyes.:)

---

