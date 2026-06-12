---
title: "Wine a Pain"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-11
I'm finding Wine a pain in the butt.

After using winetools .0.9.5 I've had no success.  I look in my windows Program File and can't find any of my games or other stuff.

I just want Galactic Civilization 1.2 to run.  

I've tried doing it this way:  jim@jim-desktop:~$ Path=C:\Program Files
bash: Files: command not found
jim@jim-desktop:~$ Path=C:/Program Files
bash: Files: command not found
jim@jim-desktop:~$ Path=C:/ProgramFiles
jim@jim-desktop:~$ Path=C:/ProgramFiles/Strategy First/Galatic Civilizations/galciv.exe
bash: First/Galatic: No such file or directory
jim@jim-desktop:~$ Path=C:/ProgramFiles/StrategyFirst/Galatic Civilizations/galciv.exe
bash: Civilizations/galciv.exe: No such file or directory
jim@jim-desktop:~$ Path=C:/ProgramFiles/StrategyFirst/GalaticCivilizations/galciv.exe

I wish the developer at Wine HQ would have better examples onhow to run apps for newbies.  I've been trying for a week now trying to get thisthing to work

---

### Post by haxer on 2006-09-11
huh... you shouldnt be able to find the c:/program folder in the "ubuntu" file system like using the termina... or?

---

### Post by Aurdal on 2006-09-11
If you've installed the program with wine, you should be able to run it with the command:

$ wine "~/.wine/drive_c/Program Files/Strategy First/Galatic Civilizations/galciv.exe"

---

