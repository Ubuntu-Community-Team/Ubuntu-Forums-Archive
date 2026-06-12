---
title: "[SOLVED] Synaptic"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by ibbill on 2008-01-27
Get the following error when opening Synaptic. Any help greatly appreciated.

---

### Post by r4ik on 2008-01-27
type,

sudo dpkg  --configure  -a

in theTerminal hit enter you're pasword will be asked fill it in and hit enter again.
That should do it.

---

### Post by mali2297 on 2008-01-27
Open a terminal and copy/paste the following code
```

sudo dpkg --configure -a

```
Press Enter.

---

### Post by jw5801 on 2008-01-27
You'll need to open a terminal and run ```
sudo dpkg --configure -a
```If that produces errors, post them here and we'll see what's going wrong!

---

### Post by bollix47 on 2008-01-27
Open a terminal (Applications > Accessories > Terminal)

Type the following:

```
sudo dpkg --configure -a
```

EDIT: oops ... slow fingers :)

---

### Post by ibbill on 2008-01-27
first off thanks for the help.

after typing  sudo dpkg --configure -a   in the terminal I get the following

---

### Post by ibbill on 2008-01-27
oops if I click okay nothing happens.

---

### Post by sumguy231 on 2008-01-27
Press enter.

---

### Post by ibbill on 2008-01-27
slaps self in face[COLOR="DarkSlateBlue"] press enter[/COLOR] omg what was i thinking thanks ever so much all is well again:oops:

Marking thread solved thanks again.

---

### Post by mali2297 on 2008-01-27
Try to open Synaptic again. If it still doesn't work, uninstall the package which seems to cause the problems.
```

sudo dpkg -r msttcorefonts

```
(You can reinstall it later.)

EDIT: Nevermind.

---

