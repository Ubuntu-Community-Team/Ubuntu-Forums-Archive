---
title: "Real newbie here"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by softwarepirate on 2005-11-23
How do i use .exe files?

---

### Post by 23meg on 2005-11-23
Windows programs? Try your luck with Wine. To install it, enter```
sudo apt-get install wine
```
To run a Windows executable with Wine ```
wine /path/to/executable.exe
```

---

### Post by darknuala on 2005-11-23
Linux doesn't use .exe files.  If you want to try and run a windows .exe file, you will need to install wine.

sudo apt-get install wine from a terminal.

after that type:  winesetup, or wine, configure it, then when you right click on an .exe file, open with wine.

You should go to [http://winehq.com/](http://winehq.com/) first, to see if your app is supported there.  Alot of apps are supported, but I believe they run alot slower in linux.  

Just out of curiosity, what .exe file are you trying to install?

---

### Post by Brunellus on 2005-11-23
[QUOTE=softwarepirate]How do i use .exe files?[/QUOTE]
quick answer:  Run windows.

Long answer:  .exe files are largely meaningless to linux.  to run them you will probably need [WINE](http://winehq.com).

---

### Post by Danielle on 2005-11-23
how does Ubuntu know the file format? i took a txt file from Ubuntu to Windows and the file had no extension, so how does Ubuntu know it's a txt file? i had to attach .txt to the end when it was in XP. i think the same thing happened with an archive ???

---

