---
title: "using wine"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-26
i have installed wine succesfuly by using

sudo apt-get install wine

now how to use it?
for example i have winrar.exe on my home/user/desktop ,which command will install it.

i've heared  that wine is graphical software.where is its icon? i mean,its shortcut like shorcuts in window

---

### Post by nanotube on 2006-05-26
afaik, you have to use wine from commandline. so to use that winrar, you open a terminal and issue command
wine /home/yourusername/desktop/winrar.exe
(if winrar.exe is the installer, rather than the actual program executable, then it will install it first, and put it into the fake drivec (in your home dir, under .wine folder), and then you can run that exe with wine.
BUT: there is no need to run winrar with wine, when you can just install rar capability onto the archive manager in ubuntu! just run
sudo apt-get install rar-nonfree

---

### Post by tkjacobsen on 2006-05-26
wine is entirely command line driven..

First of all you'll have to configure wine form a terminal type:```
winecfg
```

then you can run .exe using:
```
wine winrar.exe
```

If you want a graphical wine you can try xwine, but i'm not sure it is in the repo


Take a look at wine in the ubuntu wiki: [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

---

### Post by Kilz on 2006-05-26
Made a mistake and got 2 posts, have to learn how to delete them.

---

### Post by Kilz on 2006-05-26
[QUOTE=u04f061]
i've heared  that wine is graphical software.where is its icon? i mean,its shortcut like shorcuts in window[/QUOTE]

Wine is located in /usr/bin but it isnt a gui program.
Wine can emulate a desktop. To do that you would have to go to type in winecfg, click on the Graphics tab, and click on the Emulate a virtual desktop box, then ok. But all that will do is start programs in a wine window instead of on your desktop. It wont be a wine gui program.

---

### Post by bruce89 on 2006-05-26
Just right click on the *.exe and select Open with...
Select _U_se a custom command and type ```
wine
```

---

### Post by u04f061 on 2006-05-26
[QUOTE=nanotube]afaik, you have to use wine from commandline. so to use that winrar, you open a terminal and issue command
wine /home/yourusername/desktop/winrar.exe
(if winrar.exe is the installer, rather than the actual program executable, then it will install it first, and put it into the fake drivec (in your home dir, under .wine folder), and then you can run that exe with wine.
BUT: there is no need to run winrar with wine, when you can just install rar capability onto the archive manager in ubuntu! just run
sudo apt-get install rar-nonfree[/QUOTE]

i have installed winrar using wine but i can't open .rar files. i also created deskto icon of my winrar but it does not open

i tried to install winrar onto archieve manager but following error was made

ejaz@ejaz:~$ sudo apt-get install rar-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package rar-nonfree
ejaz@ejaz:~$

---

### Post by tkjacobsen on 2006-05-26
Before installing rar-nonfree you have to add the multiverse repository:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by AndrewCaul on 2006-05-26
Nautilus can also extract .rar archives. Just right click the file and hit Extract.

---

### Post by u04f061 on 2006-05-26
[QUOTE=AndrewCaul]Nautilus can also extract .rar archives. Just right click the file and hit Extract.[/QUOTE]

i did so but it was not able to do so.the file name was books.rar

it says

Could not open "books.rar"

Archive type not supported.

---

### Post by %hMa@?b&lt;C on 2006-05-26
sudo apt-get install unrar  
then unrar /path/to/books.rar

---

