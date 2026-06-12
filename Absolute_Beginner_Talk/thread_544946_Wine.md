---
title: "Wine"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by domat00 on 2007-09-06
What's the command to run Wine from Alt + F2 and how can I default it to install windows apps?  It should have done both automatically when I installed it, but it didn't and I haven't a clue how to make it work.

---

### Post by pay on 2007-09-07
To make it open up with wine automatically in gnome, right click an .exe file and click Properties. Go to the open with tab then click add and then use custom command. type wine and then add it. it should now automatically open wine when clicking on an .exe.

---

### Post by domat00 on 2007-09-07
That works, but when I try to run the executable, I get an "Unable to elevate, error 2" message.

---

### Post by domat00 on 2007-09-07
bump

---

### Post by zvacet on 2007-09-07
In personal folder>view>show hidden files and you will see .wine folder.Put your exe in Program Files.In terminal type

```
winefile
```

Click on C and you will see program files.Open it and find your exe and double click on it.

Second way to install is to put your exe in any folder in your home partition(just for example let it be named programs)

```
wine /home/username/programs/your program exe.
```

---

### Post by TeaSwigger on 2007-09-07
Might be a silly question but: Have you entered this in a terminal:

```
winecfg
```

to set up WINE first?

---

