---
title: "How to Copy Files using Terminal?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by yizuman on 2008-03-07
How do I use the Terminal to copy certain files into the "/usr/share/games/eduke32" directory?

The following files I need copied into the directory above are..........

"/home/whatever/Duke Nukem 3D Atomic Edition/Duke Nukem 3D/GAME.CON" and the "/home/whatever/Duke Nukem 3D Atomic Edition/Duke Nukem 3D/DUKE.GRP"

Obviously since the "/usr/share/games/eduke32" needs a superuser mode to allow files to be copied into it,

Any help is appreciated.

Thanks

---

### Post by Liet_Kynes on 2008-03-07
Typing the following into a terminal should work :)

```
sudo cp /home/whatever/Duke\ Nukem\ 3D\ Atomic\ Edition/Duke\ Nukem\ 3D/GAME.CON /usr/share/games/eduke32 
```

```
sudo cp /home/whatever/Duke\ Nukem\ 3D\ Atomic\ Edition/Duke\ Nukem\ 3D/DUKE.GRP /usr/share/games/eduke32 
```


EDIT: Yeah I've edited the commands thanks :)

---

### Post by hyper_ch on 2008-03-07
And you need to either put quotes aournd the duke nukem path or escape it with a backslash...

---

### Post by lswest on 2008-03-07
yeah, the proper commands would be (not saying what the other guy said was wrong, it was the right code, just syntax-wise incorrect):
```
sudo cp /home/whatever/Duke\ Nukem\ 3D\ Atomic\ Edition/Duke\ Nukem\ 3D/GAME.CON /usr/share/games/eduke32

sudo cp /home/whatever/Duke\ Nukem\ 3D\ Atomic\ Edition/Duke\ Nukem\ 3D/DUKE.GRP /usr/share/games/eduke32
```

or you could wrap them in quotes, either way works, but it is required as Linux does not see spaces as in the filename, but as a seperate filename/path/command, therefore you need quotes or a backslash or auto-complete the path using the TAB button (it will auto-complete the name of the folder/file as long as there are enough letters typed which apply only to one file or folder, otherwise pressing it twice will output a list of files starting with what you have entered)

---

### Post by anaconda on 2008-03-07
> **hyper_ch said:**
> And you need to either put quotes aournd the duke nukem path or escape it with a backslash...

OR use the tabulator key when writing that to terminal.. (TAB will quess the rest of the name)

---

### Post by The Cog on 2008-03-07
That tabulator is soooo useful!

If you're trying to use the command line only because you know you need root permissions, note that you can get a root graphical file manager with this command:
**gksudo nautilus**

---

