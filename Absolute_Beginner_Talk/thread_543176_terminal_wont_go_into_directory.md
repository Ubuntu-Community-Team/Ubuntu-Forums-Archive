---
title: "terminal wont go into directory"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by kubilaycan on 2007-09-04
hi i want the terminal to go into this directory

/home/kubi/.wine/drive_c/Program Files/Steam

when i do cd home/kubi/.wine/drive_c/Program Files/Steam it says no such directory

i know the problem is with the space in "Program Files" because i can go into home/kubi/.wine/drive_c without anyproblems... 

i need urgent help please!! its going on my nerves :)

thx

---

### Post by Dr Small on 2007-09-04
Try this:
```
cd "/home/kubi/.wine/drive_c/Program Files/Steam"
```
and see if it helps ;)

Dr Small

---

### Post by kubilaycan on 2007-09-04
yeahh!!! thx!

---

### Post by por100pre1 on 2007-09-04
Next time don't forget the **/** before folders:

[COLOR="Red"]/[/COLOR]home/kubi

---

### Post by Dr Small on 2007-09-04
> **por100pre1 said:**
> Next time don't forget the **/** before folders:

[COLOR="Red"]/[/COLOR]home/kubi
And quotations around an address with a space ;)

---

### Post by AnRa on 2007-09-04
Here's an alternative:```
cd /home/kubi/.wine/drive_c/Program\ Files/Steam
```

---

### Post by NT4usB on 2007-09-04
Tab Autocomplete is your friend.

Next time, try:```
cd /home/kubi/.wine/drive_c/Program
``` then hit the Tab key. 
It will complete the path for you. 
Hit Tab twice in a row to see all the folders that begin with *Program*

---

### Post by por100pre1 on 2007-09-04
[SIZE="3"]I love this trick:

Type the command (with an space after it of course) and then DRAG and DROP the folder or file from the file browser to the "terminal" window. Enjoy!
:guitar:[/SIZE]

---

