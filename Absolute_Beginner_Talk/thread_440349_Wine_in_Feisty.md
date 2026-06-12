---
title: "Wine in Feisty"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by xthund3rh3adx on 2007-05-11
hey, i have just installed WINE, and i have no idea how to set it up. I have Feisty,

I heard if WiNETOOLS but no luck for feisty. Any ideas?

---

### Post by xthund3rh3adx on 2007-05-11
please? anyone??

---

### Post by AndyCooll on 2007-05-11
Have a bit of patience mate!  Sheesh!

Once setup the Wine defaults will be fine for most things. However if you want to tweek the configuration type the following in to a command line:

```
winecfg
```

That should get you going.

:cool:

---

### Post by theicyj on 2007-05-11
Try "winecnf" in the terminal.  You could always try [Automatix]("http://www.getautomatix.com/") to easily install wine.

---

### Post by xthund3rh3adx on 2007-05-11
thanks guys, if i have any problems (god forbit) ill be back ;)

---

### Post by xthund3rh3adx on 2007-05-11
ok, well everything is fine in the setup, but how would I actually install a WinXP program? or run a WinXP .exe?

For example, I tried to execute spider.exe, a common game for winxp.

---

### Post by Cypher on 2007-05-11
You should have a ".wine/c_drive" folder and that's where you copy the .EXE files, and then execute "wine spider.exe"..

---

### Post by xthund3rh3adx on 2007-05-11
:S i cant fine that folder

---

### Post by Kazur on 2007-05-11
Try:
/home/USERNAME/.wine/drive_c

USERNAME = your username.

---

### Post by xthund3rh3adx on 2007-05-11
no, it is not there :S is this a problem?

---

### Post by dca on 2007-05-11
It's hidden, select 'view hidden files' in nautilus view options.

---

### Post by dca on 2007-05-11
Generally, if I have a packed .exe installer I was able to from the command line navigate to the directory (Desktop maybe) and do 'wine setup.exe' and it does its thing.

---

### Post by xthund3rh3adx on 2007-05-11
ok, i have noticed that there is barely anything in the "WINDOWS" folder. I remember seeing that "WINE will use WIndows DLLs if they are available" or something...so if i copy over my entire Windows folder over from my other computer will it work like windows?

PS, i am still confused how to execute .exe files, i get an error saying it doenst no what to do

---

### Post by kc0eks on 2007-05-11
Their are tons of help files on wine floating around but simply wine program.exe has worked for the most part. Also Crossover Linux works very well, and makes win32 exe's clickable like in windows, simply double click and launch the installer.

Im sure you can make wine do this too, but im not that smart just yet..and crossover works nice ;)

---

### Post by xthund3rh3adx on 2007-05-11
sadly, WINE is free and i need a free app, im gonna try the "wine spider.exe"

---

### Post by xthund3rh3adx on 2007-05-11
Cannot open /home/peter/.wine/drive_c/windows/winebrowser.exe: No application suitable for automatic installation is available for handling this kind of file.

---

### Post by Campingman on 2007-05-11
> **xthund3rh3adx said:**
> ok, i have noticed that there is barely anything in the "WINDOWS" folder. I remember seeing that "WINE will use WIndows DLLs if they are available" or something...so if i copy over my entire Windows folder over from my other computer will it work like windows?

PS, i am still confused how to execute .exe files, i get an error saying it doenst no what to do

That is going to take up a loads of space!

To get wine to install a program: navigate with the terminal to the folder with the install.exe file and input wine (name of set up exe file) wine will then install to its folder.  A menu item will then be created under applications>wine>programs.  
More information on Wine
[http://frankscorner.org/index.php](http://frankscorner.org/index.php)
It should answer all your questions.   Not all programs will run under wine, so before you pull your hair out trying to get a program to run make sure wine will support it.

---

### Post by xthund3rh3adx on 2007-05-11
um.,.....how would i use that?? (terminal)

---

### Post by Campingman on 2007-05-11
> **xthund3rh3adx said:**
> Cannot open /home/peter/.wine/drive_c/windows/winebrowser.exe: No application suitable for automatic installation is available for handling this kind of file.

I use nautilus-open-terminal (in synaptic)  it is much easier than the cd command.  When installed you can use nautilus to navigate to the folder you want and then right click, select open terminal and the terminal opens in the folder.  Much easier IMHO

---

### Post by livingtarget on 2007-05-11
**With GUI**
Try and right click, find "open with Wine" if it's there than click it. If the program runs then it works in wine if not it doesn't. You can still try it in the terminal in any case, it will give you more detailed feedback.

If you right click and it's not there choose "open with Other Application". Now at the bottom you can click and insert a custom command. Add "wine" as the command  and press open.

**Without GUI**
Open the terminal application and browse to the directory with the .exe file, for example:
> *cd /home/user_name/*

Then just type *wine program_name.exe*, for example to run the program setup.exe you can do
> [I]cd /where/your/program/is/
wine setup.exe[/I]
**-or-**
> *wine /where/your/program/is/setup.exe*

For more details on the wine command, run "wine --help" in the terminal.

Enjoy your Wine :)

---

### Post by xthund3rh3adx on 2007-05-11
thanks a lot! (still, stay posted here!)

---

### Post by livingtarget on 2007-05-11
Another quick test to see if wine is working -> press alt+f2 and insert "winemine", should give you a minesweeper clone under wine.

---

### Post by bsmith1051 on 2007-05-11
FYI - .wine is a hidden folder so you have to enable View > Show Hidden Files.  The dot in the beginning of the name is how you mark files or folders as hidden.

---

### Post by livingtarget on 2007-05-12
> **bsmith1051 said:**
> FYI - .wine is a hidden folder so you have to enable View > Show Hidden Files.  The dot in the beginning of the name is how you mark files or folders as hidden.

Press Ctrl+H to toggle this behaviour temporarily. :KS

---

### Post by psychok7 on 2007-05-12
let me see if i got this right: 
we have to go to the cd to C:\ Hard drive, and then wine one of its programs, and automatically it will "transport" the application i just chose to the .wine folder ?? 
or i have to copy past my favourite applications to wine folder?? 
isnt there a graphic interface for wine?? im under the impression i kinda used it once

---

### Post by bsmith1051 on 2007-05-14
I really don't think you need to copy/move/link anything.  You want to open a Windows-style .exe program, right, and you've already installed the Wine package?  Then right-click on the .exe, select Open With Another App, then click Choose Custom  and enter,
/usr/bin/winelauncher

That's all I had to do, at least.

---

