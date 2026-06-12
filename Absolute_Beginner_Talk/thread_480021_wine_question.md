---
title: "wine question"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-06-20
so i am trying to run a program in wine.  When i first installed the program, the program came on and worked.  now when i try to run the program with a command through the terminal i am getting  problems.

The file i want to run is located in:
/home/endlessurf/.wine/c/Program Files/MegaSquirt/MegaTune2.25

when i go to run the program i get:
 /home/endlessurf/.wine/c/Program: No such file or directory

just for fun i delete everything up to /c/ and i get:
bash: /home/endlessurf/.wine/c/: is a directory

whether this helps or not i do not know.  But i would like to run the .exe fine that is in the megatune2.25 folder.  how do i make it happen?

---

### Post by bobplano on 2007-06-20
there was a space in the folder program files so you need to put quotes around the path.

---

### Post by endlessurf on 2007-06-20
so something like this then
wine ~"/home/endlessurf/.wine/c/Program Files/MegaSquirt/MegaTune2.25/megatune.exe"

---

### Post by CaptainInsaneO on 2007-06-21
> **endlessurf said:**
> so something like this then
wine ~"/home/endlessurf/.wine/c/Program Files/MegaSquirt/MegaTune2.25/megatune.exe"

cd to your home directory and then type

```
wine './endlessurf/.wine/c/Program Files/MegaSquirt/MegaTune2.25/megatune.exe'
```

Hope this helps!

---

### Post by Clay_Banger on 2007-06-21
or you could use back slashes to use the spaces as spaces instead of breaks:
```
wine /home/endlessurf/.wine/c/Program\ Files/MegaSquirt/MegaTune2.25/megatune.exe
```

---

