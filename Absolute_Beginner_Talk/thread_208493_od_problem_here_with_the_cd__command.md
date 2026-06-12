---
title: "od problem here with the cd  command"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-07-03
if i open a terminal and type in cd /Desktop/test it tells me it can't find the folder but if i do the following it works

cd Desktop

then type  cd test  while in the desktoop folder it works

---

### Post by Jagot on 2006-07-03
```
cd ~/Desktop/test
```

The Desktop folder is not located at /Desktop.  It is at /home/<username>/Desktop.

Adding the ~ makes it go to the Desktop directory of the current user, in the same way that cd Desktop does.

cd Desktop will only work however when you are in your/home folder.  cd ~/Desktop will work wherever you are in the directory tree.

---

### Post by stevanbt on 2006-07-03
Try 
```
cd Desktop/test
```  

The first slash in your
```
cd /Desktop/test
``` 

is looking for a directory called Desktop off the root of the filesystem.

Hope this helps, Steve.

---

### Post by atoponce on 2006-07-03
[quote=lime4x4]if i open a terminal and type in cd /Desktop/test it tells me it can't find the folder but if i do the following it works

cd Desktop

then type  cd test  while in the desktoop folder it works[/quote]
Does /Desktop exist?  The forward slash marks the beginning of the root directory.  The desktop that you are after is located in your user home directory, which is /home/<user>/Desktop.  If you are already at /home/<user>, then typing 'cd Desktop' will take you there naturally, because Desktop is at ./Desktop rather than /Desktop.  './' meaning the current directory you are in.  You can also type ~/Desktop where '~' is a shortcut to your user home directory.

Did I confuse the hell out of you?  :)

---

