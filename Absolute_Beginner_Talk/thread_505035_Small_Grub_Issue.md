---
title: "Small Grub Issue"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by webster17 on 2007-07-19
Hey, i dual boot Linux/XP and my grub originally looked something like this:

Ubuntu, blah, ??.??.15
Ubuntu, blah, ??.??.15 (Recovery Mode)
Memtest
------------------------
WIndows XP

After i downloaded an update to the Linux Kernel (I think that's what did it anyway) it's like this:

Ubuntu, blah, ??.??.16
Ubuntu, blah, ??.??.16 (Recovery Mode)
Ubuntu, blah, ??.??.15
Ubuntu, blah, ??.??.15 (Recovery Mode)
Memtest
------------------------
WIndows XP


How do i go about getting rid of the old (.15) one so i just have the new one (.16) listed? Probably very simple bit for the life of me i can't work it out. :)

---

### Post by yabbadabbadont on 2007-07-19
Run synaptic, System->Administration->Synaptic Package Manager.  Search for linux-image-blah blah blah (the extra one you want to remove)  Right click on it and select "Mark for complete removal"  Hit the Apply button.  After that, it should be removed from your grub menu.

---

### Post by skymera on 2007-07-19
better

```
sudo gedit /boot/grub/menu.lst
```

just put a # before everyhting to do with .15

DONT delete it!

---

### Post by Skidpad on 2007-07-19
A good thing to do is not immediately remove the old kernel, but rather leave it in place until you use your computer for a while and verify you don't have any problems with the new kernel.

In the meantime, you can hide the old kernel entries by editing your Grub file.  Open a terminal and paste this line: sudo gedit /boot/grub/menu.lst

You can them comment out (place a # sign in front of) the old kernel entries so they will no longer appear in your Grub/boot menu.

Once sufficient time has passed, you can then open Synaptic, search for "Linux-image", and mark for removal  all of the earlier versions.  Apply changes.

---

### Post by webster17 on 2007-07-19
Puting the #'s in menu.lst worked a treat. Thanks for all the help.

---

