---
title: "Wine Problem"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by camz on 2007-03-23
hey guys, I have installed wine onto ubuntu 6.10 via the add/remove programs menu. its been installed but now I cant find it anywhere? where is it, and how can i get it up onto the applications menu.

another small question while i am here, how do you remove things from the applications menu, but keep the actual program?

thanks,
cameron

---

### Post by camz on 2007-03-23
hello please help

---

### Post by camz on 2007-03-23
please?

---

### Post by AndyCooll on 2007-03-23
Wine doesn't show up in the menu because its a behind the scenes app. It just boots into action when required, or you can run a Windoze app from the command line.

To configure Wine at the command line type:
```
winecfg
```

To run an app from the command line, it's something along the lines of:
```
wine path/to/app
```

The game I use Wine for has the following command line:
```
wine "C:\Program Files\Sports Interactive\Football Manager 2007\fm.exe"
```

:cool:

---

### Post by xopher on 2007-03-23
Im not sure about this, but for me Wine appeared in the Applications menu only after I'd installed some programs, or games as I did. To install a program/game, just cd to the /path/of/the/installer and run: ```
wine nameofapp.exe
```

> another small question while i am here, how do you remove things from the applications menu, but keep the actual program?

Right click on the 'start button' and select edit or something like that, will launch the Alacarte menu editor, then just untick the apps you don't want visible.

---

### Post by camz on 2007-03-23
Thanks!

Any way you could tell me how to remove things from the Applications list without removing the program?

---

### Post by camz on 2007-03-23
Never mind, thanks a lot guys.

---

### Post by AndyCooll on 2007-03-23
Forgot to say, you can get more info about Wine here: [Wine HQ]("http://www.winehq.com/")

:cool:

---

### Post by zvacet on 2007-03-23
Open menu layout and find program that you don´t want and just unchek it.Program will still be installed but you will  not see it in applications menu.

---

