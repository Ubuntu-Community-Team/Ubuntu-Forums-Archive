---
title: "Urban Terror Installation"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by boboyo on 2008-01-18
i downloaded urban terror4.1 (its a game) and i dont know how to install it
theres a package but i dont know what to click to install it
can anyone tell me what to do?

---

### Post by sumguy231 on 2008-01-19
You're just supposed to extract it (just click on the archive to do this) and then run the executable. Quoth the website:

> Just unzip the zip and make a shortcut to the ioUrbanTerror executable.
Mac executable: ioUrbanTerror.app
Linux 32bits executable: ioUrbanTerror.i386
Linux 64bits executable: ioUrbanTerror.x86_64
In linux, you need to make it executable first: right click it, properties and tick the 'allow execution' box.

---

### Post by boboyo on 2008-01-19
thank you alot

---

### Post by Christmas on 2008-01-19
Urban Terror is a mode for Quake 3. You can install Quake 3 from CD or install ioQuake 3 from [here](http://ioquake3.org/) and then copy the directory which contains the UrT pk3s into ~/.q3a, where ~ is your home directory. For example the path to your ioUrbanTerror.i386 file should be something like /home/your_user/.q3a/q3ut4/ioUrbanTerror.i386. The same directory (q3ut4) should contain zpak000.pk3 and zpak000_assets.pk3. 

To run UrT properly type:
```
ioquake3 +set fs_game q3ut4
```
Tell me if this works.

---

