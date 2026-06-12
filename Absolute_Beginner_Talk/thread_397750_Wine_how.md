---
title: "Wine how ??"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by mni127 on 2007-03-31
i want how to use wine 

how to run programs (media player ,, real player 10 ..etc )

:(

---

### Post by eljalill on 2007-03-31
First you have to install wine from the repositories. Use synaptics or type
```
 sudo apt-get install wine 
``` in a terminal.
Then you download the installation files for the programs you want to use, and type
```
wine yourprogram.exe 
```, once you are in that directory (navigate with cd. man cd tells you, how to use that command. Leave the manual with "q".)

However, not all windows programs run with wine.
[http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php) is a list of applications that do run.

But lastly it might be an idea to start using native Linux aplication. For media player there are several programs, which can do that same or more, try e.g. Listen, Banshee, amarok etc, and totem, gxine, vlcplayer and so on for videos. These Linux programs are generally better to use under Linux, they are more flexibel and less buggy.

---

### Post by zvacet on 2007-03-31
After yo install wine run in terminal
```
winecfg
```
that will configure wine and after that you can use it.

---

### Post by Patrick K on 2007-03-31
Winefile is handy, too.

---

### Post by mni127 on 2007-03-31
1000,000 thanks 2 u 

i am very happy cause you helped me :)

---

### Post by slingre87 on 2007-03-31
sudoslingre87@slingre87-laptop:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... DoneSearch
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
slingre87@slingre87-laptop:~$

Since there is no installation candidate (and I just had the same problem whilst trying to get tzdata) what does it mean and how do I remedy it?
Still new to Ubuntu, so I'm not quite sure what this means...any help with this is greatly appreciated. thanks

---

### Post by Sable683 on 2007-03-31
or you can ust click on your main menu icon, select Add/Remove, when the window opens, type "wine" in the search location, then select show "all available applications", then click on "apply", type in your password and it should down load everything you need.

---

### Post by slingre87 on 2007-03-31
did that and nothing came up when I searched "wine"

---

