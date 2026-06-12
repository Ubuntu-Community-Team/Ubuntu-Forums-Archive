---
title: "wine problem"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by dave.galaxian on 2008-01-04
i have a problem starting a program in wine everthing seems to have installed ok but when i try and start the program i get a application error which says 

EExternalException in module KERNAL32.dll at 00023f50

i have try'd putting kernal32.dll into windows and have also try'd putting it into the program folder with same error everytime 

the program is Newsleecher

---

### Post by frup on 2008-01-04
That message is coming if you type wine "path/to/program.exe" in terminal? 
The kernel32.dll you are talking about that you tried moving in to wine folders is an official MS one or the wine one? sometimes using native .dll files can make things work.

You could try downloading a ReactOS iso and try running that in a vitrual machine and see if that runs it. ReactOS has more kernel support I believe.

If none of that works you should wait for a newer version of wine. Check the AppDB at wineHQ.org and see if the program is mentioned and what other people may have experienced with it, maybe there are some work arounds. 

If the AppDB has no record maybe you should open one up and even become a maintainer for the program.

---

### Post by dave.galaxian on 2008-01-04
yea thanks frup it is listed with problems this is all for the wife so she can d/l nzb files easy anyone know of a program that i can use in ubuntu instead with a easy interface for her to use so i can drop using trying to get it to work

---

