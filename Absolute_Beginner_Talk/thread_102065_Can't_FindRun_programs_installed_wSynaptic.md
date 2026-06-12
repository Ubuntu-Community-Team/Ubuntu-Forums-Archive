---
title: "Can't Find/Run programs installed w/Synaptic"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Barney on 2005-12-11
I have installed several programs using the Synaptic Package Mananger, and all went well.  However, I can't find how to execute and run them.  Ex. Gnucash.

---

### Post by Turtle.net on 2005-12-11
Hi,
Have you tried to launch these programs using command line ?

Sometimes it seems that gnome doe not include automatically your new application in the "Applications" menu.
You can edit and modify this menu by typing smeg in a terminal.
If it shows your application should be there you can try
```
killall gnome-panel
```
That will reset the gnome panel and all the menus (this execution is safe, don't worry, I do that quite often ;) )

---

### Post by teaker1s on 2005-12-11
search the installed package then highlight it and select installed files tab eg.3dchess

/usr/games/3Dc
 


if it will load when you copy and paste it to terminal thats the path you will need for a launcher

---

### Post by kori.mendocino on 2005-12-11
open up your terminal, then type a the first few letters of the program you're trying to run, then press tab once if it's the only command* with there first letters, or twice to see all the command with these two letters.

* once a program is installed in your $path, it becomes a command, e.g. you can issue it any time from anywhere on your pc or network, with any parameters, supported by it.

---

### Post by Barney on 2005-12-11
I searched Synaptic, found the installed files, and command line worked (Gnucash).  I also tried the same technique with the file browser and wasn't successful that way.

smeg didn't find gnucash and 'killall gnome-panel' didn't work

"learning the hard way here, too!'

---

### Post by Barney on 2005-12-11
kori...........

GREAT!  Thx

"Now, why didn't I think of that(?)!"

---

### Post by Turtle.net on 2005-12-11
And now you can create launchers with smeg to have your favorite applications in the gnome menu ;)

---

