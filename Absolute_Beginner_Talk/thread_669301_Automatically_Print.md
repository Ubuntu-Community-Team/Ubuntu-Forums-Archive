---
title: "Automatically Print"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by markyb86 on 2008-01-16
Is it possible to automatically print any documents I stow in a folder? Im printing to pdf in virtualbox windows xp and saving it to my linux desktop. is it possible to print a pdf file automatically? or is there a folder that you can save to that will autoprint?

---

### Post by blueridgedog on 2008-01-16
You could print them with the lpr command (type man lpr in a terminal for more informaiton).  Once you developed a command you were satisfied with you could put the command in your crontab file so that one an hour it printed all the contents of the folder, but avoiding duplicating those that had already been printed would require a script of some other management on your part.

Something as simple as 
```

lpr /my/folder/path/* 
```

Would be a good start.

---

