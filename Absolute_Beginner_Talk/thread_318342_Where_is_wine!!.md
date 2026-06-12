---
title: "Where is wine!?!?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-13
I installed wine and all but how do i run it theres no shortcuts to it is there a terminal command

---

### Post by ciscosurfer on 2006-12-13
> **synt4xerr0r said:**
> I installed wine and all but how do i run it theres no shortcuts to it is there a terminal commandHere's the main Wine site that will help guide you in using Wine: [http://www.winehq.com/](http://www.winehq.com/)

Generally speaking, you can issue something like this to get your Windows app running```
wine windowsGame.exe
```Your Wine files are located under your home directory and is hidden: ~/.wine

---

### Post by Frak on 2006-12-13
KDM makes the menu automatically, but one: use winecfg and two: you can use nautilaus to find the program you want and execute it automatically

---

### Post by ciscosurfer on 2006-12-13
Issuing winefile is also helpful, but yes, you should winecfg before you try to use Wine```
winecfg
winefile  #to look at your files in a Wine environment
wine windowsApp.exe
```

---

### Post by synt4xerr0r on 2006-12-13
Thanks for all the help i was starting to think that u had to have windows on ur hdd for wine to config the stuff LOL!!!

---

