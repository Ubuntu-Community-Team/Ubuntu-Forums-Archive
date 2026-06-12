---
title: "Would love some help!"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Travis031684 on 2007-10-10
I am new to ubuntu and I am trying to set it up so that I can dual boot. I have the cd burned and it works fine (I am typing this message in firefox using linux) but when I click on the install link I get all the way through the set up, through to selection of partitioning and that process, through the user import section, I click on install and i gets about 1/4 of the way done and then a message pops up that reads 

"The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/My\040Book

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?"

When I choose the options it gives me, it just takes me back to the partitioning screen. I have no idea what to do or how to fix this, and I am pretty down because I really want to start using ubuntu!  Please help!

---

### Post by defrex on 2007-10-10
What partitioning option are you selecting when asked? Also, do you currently have multiple partitions, or is it currently windows on the whole disk?

The error message itself mentions it, but make sure you don't have anything open that might be using the disk, like the partition editor (gparted), or window manager (nautilus).

---

### Post by Gazneth on 2007-10-10
I just installed 7.10 Beta myself when a similar error popped up I just clicked continue and continued the install.  The error you got I think comes from the settings import wizard. If you used it, try another install without it, you may still get the error but the install should work.

---

### Post by Incense on 2007-10-10
> **Travis031684 said:**
> I am new to ubuntu and I am trying to set it up so that I can dual boot. I have the cd burned and it works fine (I am typing this message in firefox using linux) but when I click on the install link I get all the way through the set up, through to selection of partitioning and that process, through the user import section, I click on install and i gets about 1/4 of the way done and then a message pops up that reads 

"The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/My\040Book

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?"

When I choose the options it gives me, it just takes me back to the partitioning screen. I have no idea what to do or how to fix this, and I am pretty down because I really want to start using ubuntu!  Please help!

I think your nameing is off.

Try changing this

```
/media/My\040Book

```

to this

```
/media/my040book
```

if you can.

If not, then try not exporting settings as stated.

---

