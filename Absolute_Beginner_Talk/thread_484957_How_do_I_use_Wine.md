---
title: "How do I use Wine"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by dptxp on 2007-06-26
I am downloading wine but I do not know how to install Windows Programs in it OR how to run them.
Any help ?

---

### Post by Pobega on 2007-06-26
From the command line, just type
```
wine /path/to/exe
```

If the .exe file is an installer, the installer will run and install the program into a virtual C:\ drive, which is located in *~/.wine/drive_c/*

When you want to execute the installed program, it should be something like this:
```
wine ~/.wine/drive_c/Program\ Files/yourprogram/yourprogram.exe
```
You may have to check out the *~/.wine/drive_c/Program Files* directory yourself, to see what the programs folder is called and what the executable is named.

---

### Post by njknight on 2007-06-26
If you already have the windows application in a folder (in your home folder or perhaps the desktop) then one way would be to just open a terminal window and type the word "wine" (without the quotes and also add a space after the word wine) then open the folder that contains the windows application and drag and drop the windows .exe file into the terminal window.  Click into the terminal window and press return...that's it

---

### Post by dptxp on 2007-06-26
Thanks. Real fast reply.

Shall try once Wine is installed in next 5 to 10 minutes.

So no GUI ? No Menu ? Have to run using terminal ?

---

### Post by Lord Illidan on 2007-06-26
In nautilus, you can just click on an .exe and it will pop up wine. But I and many other users prefer using the terminal to pass switches to the program, or use nice to set the program's priority.

What are you planning to use wine for?

---

### Post by Outrunner on 2007-06-26
There is a GUI, simply type this in the terminal
```

winefile
```

Personally, I find it easier to use the terminal.

---

### Post by M!K3_$ on 2007-06-26
if the program is on your desktop, you can "right-click" on it and open it w/ another program. then type in wine when it wants you to find the program. then by default afterwards whenever you "left-click" on and .exe file it will use wine 

viola

---

### Post by dptxp on 2007-06-26
Thanks to everyone.

I want to use Wine for

1) In System Programming of Microcontrollers. The software is available for Windows only.

2) I have IBM WEBSPHERE STUDIO. It is now a bit old, not a great software, but it is easy to
use and I use it for designing pages for a couple of FREE websites I host. I have a Linux version
too but that actually runs under wine (maybe installs it with the program).

3) For WavePad. I like this audio recorder/converter/editor.

I also have to run a couple of DOS programs, I love them for their simplicity. One is ORCAD for PCB
layout (1990 make). I installed dosemu but could not figure out how to use it.

---

### Post by gmanlivid on 2007-06-26
i got a good question. i just installed Feisty on my laptop but i dunno how to install wine. when i try it says i need some other program installed or something like that. wat all do i need to get WINE up and running?

---

### Post by dptxp on 2007-06-26
Wine is in applications>add/remove.
I just installed it.
Now shall try to run.

---

