---
title: "How do i uninstall then reinstall Ubuntu"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Brii on 2008-04-02
Because i messed up the version saved onto my hard drive  and i want to reinstall it because you cant see any thing on it

*go look at my other post to see about it ;)

---

### Post by Crafty Kisses on 2008-04-02
> **Brii said:**
> Because i messed up the version saved onto my hard drive  and i want to reinstall it because you cant see any thing on it

*go look at my other post to see about it ;)

I don't think you have to reinstall, what do you mean you can't see anything? It's just black or what?

---

### Post by Brii on 2008-04-02
You cant see anything 

its like if theres a bunch of lines going across and there the colors of how ubuntu looks but there all out of order and weird 

something like this 
[http://www.winmobiletech.com/kuvat/E125MessedUpScreen.bmp.png](http://www.winmobiletech.com/kuvat/E125MessedUpScreen.bmp.png)

but if you move the mouse you can see something move

im using vista and it works fine *not that i like vista more that ubuntu

---

### Post by ugm6hr on 2008-04-02
Exactly the same way you installed the first time.

Just remember to format the Ubuntu partition from GParted before going through the install process, because Ubuntu doesn't seem to like to write over itself (or so it appeared the last time I tried).

---

### Post by Brii on 2008-04-02
> **ugm6hr said:**
> Exactly the same way you installed the first time.

Just remember to format the Ubuntu partition from GParted before going through the install process, because Ubuntu doesn't seem to like to write over itself (or so it appeared the last time I tried).

What do you mean GParted

---

### Post by ugm6hr on 2008-04-02
> **Brii said:**
> What do you mean GParted

In the System Menu of Live CD - Partition Editor.

---

### Post by Brii on 2008-04-02
how do i actually format the Ubuntu partition from GParted before i install it

---

### Post by Xiong Chiamiov on 2008-04-02
GParted should be in one of the menus somewhere, perhaps named something like "Disk Partitioner" (I'm not familiar with gnome).  You'll click the partition you want to reformat, then go to Partition -> Format To -> ext3 (see [here]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")).

---

### Post by CloudFX on 2008-04-02
It's quite simple... I do it quite often myself.

1. Insert and boot up from the Live CD.
2. Open up Terminal (Applications > Accessories > Terminal).
3. Type in:
```
gksu gparted
```
4. GParted will now load.  Now you must look through your partitions and declare which one is Ubuntu.  For me, there are 4 partitions all connected to a single one.  You will need to delete the entire thing.  For me, I am unable to delete all of them at once through the main partition, but deleting them one by one eventually got rid of the Ubuntu partition.  You should now have quite a large amount of unallocated space.
5.Run 'Install' from your desktop.  Go through the normal installation procedures.  When you get to the partitioning section, simply select the option to use the largest section of unallocated space.

No partitioning will be required, and Ubuntu will fully install fairly quickly!

---

### Post by Erin on 2008-04-07
So why not just go and adjust the display settings rather than reinstall? Reinstallation is a Microsoft technique not needed with Linux.

---

