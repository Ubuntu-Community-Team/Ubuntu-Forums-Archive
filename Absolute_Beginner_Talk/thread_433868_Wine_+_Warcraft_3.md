---
title: "Wine + Warcraft 3"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by vudoo on 2007-05-05
Hi, I'm very new to Ubuntu+Wine Scene I just installed Ubuntu yesterday and wine today. I need on how to install Warcraft 3 onto my computer. I have wine installed. I looked at many HOWTO but i don't really understand it.

---

### Post by Outrunner on 2007-05-05
From your post I understand that you've tried to follow a HOWTO and the results were... minimal, I guess. Can you provide a link to the HOWTO you've tried? Maybe I or someone else can clear things up for you.

---

### Post by vudoo on 2007-05-05
I looked at this one

[http://ubuntuforums.org/showthread.php?p=2586178](http://ubuntuforums.org/showthread.php?p=2586178)

and 

[http://am-productions.biz/docs/warcraft3.php](http://am-productions.biz/docs/warcraft3.php)

and

[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

im not sure how to mount the disk and make it install

---

### Post by Outrunner on 2007-05-05
If you type
```

ls /media/
```

in the terminal, do you see a referace to cdrom or cdrom0? If so that is where you're CD/DVDV drive is mounted. From there you just do
```

wine /media/cdrom/install.exe
```

---

### Post by vudoo on 2007-05-05
cdrom  cdrom0  disk
i get that in different colors is that suppose to be right?

---

### Post by Outrunner on 2007-05-05
Yes indeed, try my next command to start installing.

---

### Post by vudoo on 2007-05-05
my friend you are genius you got it working for me!!! thanks

---

### Post by Outrunner on 2007-05-05
Sure, no problem. You might have problems starting the game or playing. If so, just come back and post details

---

### Post by vudoo on 2007-05-05
how do i make it so it starts up in OPENGL mode? and where is warcraft installed into which directory so i can browse to it and edit the movie files? thankx

---

### Post by Outrunner on 2007-05-05
It's installed in .wine/drive_c/Program Files/Warcraft. The last folder name is just an assumption, because I don't know the default folder name.

Anyway to start the game in opengl mode

```
wine .wine/drive_c/Program\ Files/Warcraft/war3.exe -opengl
```

NOTE that you'll need a \ if a folder name has two or more separate words, so  .wine/drive_c/Program\ Files/Warcraft III would have a \ between Warcraft and III

```
wine  .wine/drive_c/Program\ Files/Warcraft\ III/war3.exe -opengl
```

EDIT: Also to use nautilus(or another file manager, like thunar) to move things around easily in you're Warcraft directory you'll just have to do

```
gksudo nautilus
```

NOTE -to see hidden files like .wine(that start with a dot '.') press CTRL+H

---

### Post by vudoo on 2007-05-05
lol im not sure where .wine is... so i can brose to warcraft folder lol

---

### Post by Outrunner on 2007-05-05
check out my last post again, I've edited it with the necessary info.

---

### Post by vudoo on 2007-05-05
can you point me where to go with this screenshot
[http://img527.imageshack.us/my.php?image=screenshotzb6.png](http://img527.imageshack.us/my.php?image=screenshotzb6.png)
i did ctrl+h nothing showed up

---

### Post by Outrunner on 2007-05-05
Yes well you see, you have to be in your home directory. from where you are now go to home->[your user name]-> CTRL-H and you should see .wine

---

