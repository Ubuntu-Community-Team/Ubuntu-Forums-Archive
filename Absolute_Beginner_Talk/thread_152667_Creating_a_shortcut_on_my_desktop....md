---
title: "Creating a shortcut on my desktop..."
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-03-30
I finally got Steam installed using Wine 9.7.  How would I create a desktop shotcut for it?  It's located at /home/*****/.wine/drive_c/Program\ Files/Steam/steam.exe

Thanks for the help.

---

### Post by frodon on 2006-03-30
The easiest way if you use gnome is a simple drag&drop with the middle click through nautilus (the file browther).
Anyway, this command line will do the job : ```
ln -sf /home/*****/.wine/drive_c/Program\ Files/Steam/steam.exe $HOME/Desktop
```

---

### Post by echo $USER on 2006-03-30
Thanks for the line.  That did the trick.

---

### Post by Chudilo on 2007-09-13
Thanks a lot for this post. I felt so embarrased that I wasn't drag and drop stuff to the desktop  on Ubuntu when I was showing it to someone.
I kept getting the "filename" can not be moved because you do not have permissions to change it or it's parent folder error.
And it wasn't making any sence.
Does anyone else think that that shoudl be a usability issue and the message or behavior should be changed to what one would expect from other operating systems

---

### Post by ntlam on 2007-11-12
coollllllll

---

