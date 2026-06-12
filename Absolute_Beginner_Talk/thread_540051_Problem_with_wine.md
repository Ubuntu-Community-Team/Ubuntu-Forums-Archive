---
title: "Problem with wine"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Deedlit on 2007-09-01
I tried opening a file that is a windows type file, and when it tried to install it gave me a little box that said error 0x80020005.  What should I do now?

---

### Post by quinnten83 on 2007-09-01
Hi, 
not all programs work in wine. So try first on the wine website to see if your program will work.
You can also ask there if there are any solutions to the problem.
Also, if you say here which program it is, people can help you better. Right now your question is not specific enough.

---

### Post by aldenhg on 2007-09-01
First, make sure you have wine installed. Run sudo apt-get install wine in a terminal. Once it's installed, run winecfg in a terminal. For the time being, just close it as soon as it opens. Now navigate the terminal to the folder where the .exe you want to run is. run wine yourfile.exe and see what happens.

---

### Post by Deedlit on 2007-09-01
Wine is installed per terminal, winecfg came up, when I tried to run wine hstinst.exe I got module not found.

---

