---
title: "Gaining access to a restricted folder."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-12-11
I'm trying to open a game (PlaneShift) and it doesn't seem to work.
I get this error when i try to open the folder or game.

[IMG]http://i6.tinypic.com/7wsja8o.png[/IMG]

Question is;
How do i gain access to it?

Thanks in advanced.

---

### Post by spiderbatdad on 2007-12-11
are you trying to run the program? If so, looks like it needs to be made executable
```
sudo chmod a+x /where/ever/Planeshift
``` that is, "where/ever/Planeshift" is the path to the file you are trying to run, probably /usr/bin/Planeshift. Typically, you might run the program from the terminal:
```
./Planeshift
```

---

