---
title: "[SOLVED] Compiz Fusion (again sorry)"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-07
How do you make the cube be a cube? instead of it just folding out into 4 windows.

---

### Post by Fraser from Scotland on 2008-01-07
gads please help, Its pretty annoying, even just a link to guide.

---

### Post by perlluver on 2008-01-07
Press ctrl-alt-right mouse button.  Or just press both mouse buttons at the same time.

---

### Post by sowelie on 2008-01-07
Sounds like you have the desktop wall enabled.  Do you have the compiz configuration app installed? If so it's in system -> preferences -> advanced desktop effects settings.  If not run the following command:

```
sudo aptitude install compizconfig-settings-manager
```

Then you can disable the desktop wall and enable the desktop cube and also rotate cube.

---

### Post by esodin on 2008-01-07
I am not sure I understand your problem, but here are some tips that might help you (I assume you are using Gutsy):

Select "Control Center" > "Advanced Desktop Effects", this should give you access to all the Compiz settings.

There should be a check box by "Desktop Cube" and by "Rotate Cube"

Select "Rotate Cube" and the "Actions" tab. Here you can find and change the key combinations that will let you rotate the cube.

If it does not look like a cube it bay be because you are using a "Horizontal Virtual Size" of 2 - this should be 4 (for a cube). Select "General" (still under "Control Center" > "Advanced Desktop Effects") and the Desktop Size" tab to change the value.

If you select "Desktop Cube" and the "Actions" tab you should be able to see what key combination that unfolds the cube.

Good luck!

---

