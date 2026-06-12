---
title: "[SOLVED] /etc/X11/xorg.conf is MIA"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-02-14
Its empty......


but everything is still working....


My extra mouse buttons shouldn't be working if its empty.....


should it??


odd...

---

### Post by emarkd on 2008-02-14
Are you sure it's empty? If you've mistyped the path, most text editors will bring up a blank new file.  A common mistake is to not capitalize the X in Xll

---

### Post by LostMagix on 2008-02-14
```
sudo gedit /etc/X11/xorg.conf

```

---

### Post by LostMagix on 2008-02-14
[ATTACH]59623[/ATTACH]


what do you make of this....


i got the file, but the old ones gone....

---

### Post by emarkd on 2008-02-14
Got me then ;)  I've no idea...

---

### Post by emarkd on 2008-02-14
Linux tends to cache open files instead of locking them.  That's why you can delete/move/rename things that are in use.  It's also why the update process is much smoother than with Windows.  Did you do anything to delete the file?  and have you rebooted or restarted X lately?  I'm glad you've got that original there, because you may need it to get X to start next time...

---

### Post by LostMagix on 2008-02-14
I was trying to get my ATI driver working, but its the damnedest thing. i was ably to reboot without any problems, with no /etc/X11/xorg.conf


Whats up with that?

---

### Post by oedha on 2008-02-14
is it possible.....accidentally hidden ?
what if ctrl+h

---

### Post by LostMagix on 2008-02-14
err...

I was gonna say my system was magic, but then you had to go and ruin it >;(

---

