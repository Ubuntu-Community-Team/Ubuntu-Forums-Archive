---
title: "creating a clam shortcut"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-10-23
when I installed firestarter in feisty I got a shortcut, but not one for clam. How do I get one ? TIA

---

### Post by Paul820 on 2007-10-23
If clam is in your menu, right click on it and the click 'add this launcher to desktop

---

### Post by pdlethbridge on 2007-10-23
its not, thats why the problem.

---

### Post by Paul820 on 2007-10-23
Right, from the terminal type

> whereis nameOfProgram

Replace nameOfProgram by the name of the clam program, probable clam or clamAV. That will give you the path to it. Now right click on the desktop and create a launcher there. Assuming that's where you want it. Browse to where clam is and choose an icon for it.

To make one in the menu, go to System->Preferences->Main Menu, choose where you want to put it from selecting say System Tools on the left had side. On the right, choose new item, browse to the program with the path that the terminal provided. Choose your icon.

---

### Post by pdlethbridge on 2007-10-23
still can't do it.

---

### Post by Paul820 on 2007-10-23
Why? Where are you having problems?

---

### Post by dougleduck on 2007-10-23
I dont think clamav has a gui by default. I think there are ones out there but its normally just a command line scanner using the command

$ clamscan

Try

$ man clamscan

for documentation.

You could still make a shortcut in your menus. Right click on the menu and click Edit Menus, then New Item, and write *clamscan* in the command box, and give it a name (probably clamav). 

Edit: I think you wanted one on desktop, so just right click and add laucher and same as above.

---

### Post by pdlethbridge on 2007-10-23
that didn't work either. I could create the shortcut but it wouldn't work

---

### Post by dougleduck on 2007-10-23
It may have been working, but I think this starts up clamav without opening a terminal window. You can check when you start by running the command 

$ top

which lists the hardest working processes.

Does the command 

$ clamscan 

actually work? You should get some kind of output in the terminal.

---

### Post by pdlethbridge on 2007-10-24
The funny thing about this is I have had a shortcut for clam on previous installs, possibly its something I forgot to install???

---

### Post by sayuki288 on 2007-10-24
drag the icon to the desktop like windows

:lolflag:

---

### Post by pdlethbridge on 2007-10-24
got no icon to drag anywhere, if I could I would.:)

---

### Post by pdlethbridge on 2007-10-25
Well, I was right. I hadn't downloaded all the clam files. I have my icon now. Just don't know which file it was in. If it had clam in the name, I installed it.:)

---

### Post by dougleduck on 2007-10-25
The only one besides clamav needed is clamtk. This gives clamav a GUI. This looks a pretty good one actually.

---

