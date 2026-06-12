---
title: "Ubuntu slow ?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-12
Hi.

I've just formatted my computer totally and installed ubuntu again. Now i've updated and rebooted, but ubuntu is a lot slower to open programs and to react to what i do, than it was before i formatted my computer. 

Is there a reason for this, and is there something to do about it ?

---

### Post by twiceasworn on 2007-07-12
Have you installed the drivers for your video card?  If not, that is probably the issue.

---

### Post by greg_g on 2007-07-12
Also, I would check your swap usage, ie: make sure it is there.

---

### Post by czepluch on 2007-07-12
> **greg_g said:**
> Also, I would check your swap usage, ie: make sure it is there.

How do you check swap usage ?

---

### Post by sad_iq on 2007-07-12
> **czepluch said:**
> How do you check swap usage ?
Type **free** in a terminal and see if there is a line with _swap_ in there!!!

---

### Post by czepluch on 2007-07-12
> **sad_iq said:**
> Type **free** in a terminal and see if there is a line with _swap_ in there!!!

There is. But it concerns me that it says that its all free and no space used ? Is that right?

---

### Post by czepluch on 2007-07-12
> **czepluch said:**
> There is. But it concerns me that it says that its all free and no space used ? Is that right?

             total       used       free     shared    buffers     cached
Mem:       1286264     849284     436980          0      20244     562724
-/+ buffers/cache:     266316    1019948
Swap:      1951856          0    1951856

---

### Post by sab0403 on 2007-07-12
That means there is a swap, but none of it is used (yet). So the OS hasn't used up all of your RAM.

If you do a <Ctrl>+<Alt>+F1, which takes you to the command prompt, does it still feel slow as molasses? Try opening some documents with nano, playing some music... btw you can return to the GUI with```
sudo startx
```If the GUI is guilty of the slowdown, perhaps it's your video card drivers, or maybe GNOME isn't running properly... try and notice if it takes too long to start (GNOME, not the PC).

---

### Post by czepluch on 2007-07-12
> **sab0403 said:**
> That means there is a swap, but none of it is used (yet). So the OS hasn't used up all of your RAM.

If you do a <Ctrl>+<Alt>+F1, which takes you to the command prompt, does it still feel slow as molasses? Try opening some documents with nano, playing some music... btw you can return to the GUI with```
sudo startx
```If the GUI is guilty of the slowdown, perhaps it's your video card drivers, or maybe GNOME isn't running properly... try and notice if it takes too long to start (GNOME, not the PC).

It takes me very long time to start GNOME. about 30 second. and before the formatting only 5.

---

### Post by czepluch on 2007-07-12
What should i do to get it running normal again?

---

### Post by czepluch on 2007-07-12
bump

---

### Post by czepluch on 2007-07-12
bump

---

### Post by angryfirelord on 2007-07-12
30 seconds to boot gnome? That's slow.

First, apply all updates if you haven't done so. There are some gnome updates which may speed it up.

Next, if you have a 3D capable card, install the 3D drivers for it. That seems to speed things up.

If those don't work, then go to System-->Administration-->Services.

-Disable bluetooth if you do not need it.
-Disable hplip if you do not use a HP printer.
-Disable cups if you do not use a printer.

Also, when Ubuntu is loading, is the hard drive access real heavy? It could be a rogue process like *find* or *updatedb* is getting loaded at boot.

---

### Post by czepluch on 2007-07-12
> **angryfirelord said:**
> 30 seconds to boot gnome? That's slow.

First, apply all updates if you haven't done so. There are some gnome updates which may speed it up.

Next, if you have a 3D capable card, install the 3D drivers for it. That seems to speed things up.

If those don't work, then go to System-->Administration-->Services.

-Disable bluetooth if you do not need it.
-Disable hplip if you do not use a HP printer.
-Disable cups if you do not use a printer.

Also, when Ubuntu is loading, is the hard drive access real heavy? It could be a rogue process like *find* or *updatedb* is getting loaded at boot.

I dont think any of that is the reasin, but my swap drive is not getting used. I think that is the reason, but what can i do to use it ?

---

### Post by angryfirelord on 2007-07-13
Actually, if your swap is getting used, that would be the problem. Unlike Windows, Linux uses swap only when it has to because the hard drive is so slow.

It could also be an install gone bad. If the hard drive access is not super heavy, did you try using the alternate cd?

---

