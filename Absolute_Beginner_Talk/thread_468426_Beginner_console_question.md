---
title: "Beginner console question"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by l1oyd on 2007-06-08
So after getting lost in the forum for only 3 hours I've decided to ask a question:

If I run a program from console for example "pidgin" the program opens, the cursor jumps down a line and then I can't use the console session again. Every (very few) command I know does nothing.

Cheers

---

### Post by pavpan on 2007-06-08
add & to the end of a command to make it run in the background. Basically, the terminal and console will run while the command you entered does whatever it needs to do. Or you can press Alt+F2 to open Run and run any command from there, then continue using the terminal (if you're in the GUI that is...)

---

### Post by drowner on 2007-06-08
The console you are running the program from is busy running the program.

If you close pidgin your prompt will return.

If you want to use another console. open another one.

---

### Post by l1oyd on 2007-06-08
Wow very quick responses, thank you both very much. 

I now know how to fix my problem and am a tiny bit more educated as to why I had a problem. 

Again thank you.

---

### Post by mayamaniac on 2007-06-09
anyone know how to open a folder window from the terminal? In OSX, if I type "open /var", it would open that folder in the Finder. Its there an equivalent command in Ubuntu? It's useful for opening hidden folders.

---

### Post by lawr_rawr on 2007-06-09
> anyone know how to open a folder window from the terminal?

If you are using Nautilus, you can type the following in a terminal:
```
nautilus <path>
```

Or, to open a folder with root permissions,
```
gksudo nautilus <path>
```

---

### Post by mayamaniac on 2007-06-09
that works, thanks. :)

---

