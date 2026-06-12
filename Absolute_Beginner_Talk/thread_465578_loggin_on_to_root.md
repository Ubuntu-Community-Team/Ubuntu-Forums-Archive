---
title: "loggin on to root?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by sneeker on 2007-06-05
ok root...  i need help i wanna put some files into my gimp folders, it says i dont have the right permissions, my guess is that i need to get into the root (windows term = administrator) HOW DO I DO IT!!???!!???

---

### Post by diatribe on 2007-06-05
sudo is the command to run things as root, ie sudo cp whatever.txt /var

---

### Post by sneeker on 2007-06-05
ooh ok, so... i guess that doesnt do wat i wanna do, im tryin to put downloaded brush files into the gimp brushes folder and it tells me i dont have the right permissions

rrg.

---

### Post by Nekiruhs on 2007-06-05
Then type 
```
sudo chown $USER /path/to/files/ && chmod 744 /path/to/files/
```
If you want normal ownership for yourself.

---

### Post by taurus on 2007-06-05
Save it to your ~/Desktop first and then run "gksudo nautilus" from a terminal and just drag 'n drop it to wherever you want to move it.

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by sneeker on 2007-06-05
```
gksudo nautilus
``` WORKED THANK YOU THANK YOU!!!!

now about my resolution... jk i think ive got that one fixed   (crossing my fingers)

---

