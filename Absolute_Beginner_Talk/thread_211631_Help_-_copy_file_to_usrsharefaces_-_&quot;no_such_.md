---
title: "Help - copy file to usr/share/faces - &quot;no such directory&quot;"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by petersjm on 2006-07-08
Hi all,

I'm trying to copy a PNG file to usr/share/faces from the Desktop but when I do so the terminal says "cp: cannot stat 'FILENAME.png': No such file or directory"

I've tried

```
sudo cp home/USERNAME/Desktop/FILENAME.png usr/share/faces/FILENAME.png
```

but it can't seem to find the original file. Can anyone help me out? When I tried to copy in the graphical mode by drag and drop, it says I don't have permission, that's why I tried the command line sudo...

---

### Post by someusernoob on 2006-07-08
Try instead of home/USERNAME/Desktop/FILENAME.png

```

Desktop/FILENAME.png

```

Or when you want to do it the graphical mode way, type this in the terminal:
```

gksudo nautilus

```

This wil open the filemanager with root access. Close it when youre done, and do not delete random stuff.

---

### Post by steve.horsley on 2006-07-08
Unless you put a slash at the start of the filename, it is looked for from the durrent directory. So if you are currently in /home/USERNAME, it would try to copy the file:
/home/USERNAME/home/USERNAME/Desktop/FILENAME.png
which it probably won't find. try this:
```
sudo cp /home/USERNAME/Desktop/FILENAME.png /usr/share/faces/FILENAME.png
```

---

### Post by petersjm on 2006-07-08
Excellent - thanks to both of you! You've solved my problem :) I'm still learning (migrated from WinXP last week!) and it's things like this that I wouldn't know if it weren't for forums like this :D

---

