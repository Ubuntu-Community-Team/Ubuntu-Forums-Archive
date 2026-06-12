---
title: "wine help!111"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by illbashu on 2007-09-01
ok, so i installed wine (useing the package manager) and and used it to install agame called "continuum" well the thing is i have no clue how to open the file after i installed it, the installed made a desktop short cut but it doesn't work...:( 

how do i open and use that game? can some plz help me! i am really stuck! :(

---

### Post by Daveth on 2007-09-01
you can usually get them going by typing in a terminal

```
wine continuum 
```

if it throws an error about not finding it, navigate to the wine folder /home/.wine/drive_c/program\ file/continuum, or wherever it is installed, and launch that same wine command from there.

---

### Post by MenZa on 2007-09-01
Wine creates a virtual C-drive in /home/yourusername/.wine/drive_c --- the structure of files in here is exactly the same as you're used to in Windows.

Do *cd ~/.wine/drive_c*, then navigate to the folder the game is installed in (most likely Program Files/something), then do:

```

wine *filename.exe*

```

I also suggest you use the latest versions of Wine at all time. This is available from [Wine's own repositories](http://www.winehq.org/site/download-deb).

---

### Post by illbashu on 2007-09-01
i cant seem to find the folder,....

---

### Post by Majorix on 2007-09-01
You have to press CTRL+H for the folder to become visible. Its hidden by default, donno why.

---

### Post by illbashu on 2007-09-01
o... i though something was wronge so i reinstalled it and not it says this 

Warning: could not find DOS drive for current working directory '/home/illbashu', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\Continuum0.39pr1Setup.exe": Module not found

EDIT!
i got it to go back to normal but i still cant launch the game :'( even from the program folder

---

### Post by Daveth on 2007-09-01
type 
```
winecfg
```
in a terminal. You will see an option under the Applications tab, to "use" different Windows versions as a default. Try one of the options and see if WINE will behave.

also, have a look at

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

---

