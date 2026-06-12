---
title: "How To Run Programs Wine Installed"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-02-23
How do I run a program wine installed?

---

### Post by dabear on 2006-02-23
If wine is installed, you should be able to double click the programs .exe file, which you will find in the .wine directory

Go to nautilus, pres ctrl + h to show all hidden files, locate «.wine»
OR
Alt + F2 and type inn «.wine» (no quotes)

Find the folder «drive_c» and «Program Files» inside. Double click the exe file.

If the program stops responding, press alt + f2 and then type «killall -KILL wine-preloader» (no quotes) to stop it

---

