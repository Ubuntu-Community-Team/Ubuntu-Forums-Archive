---
title: "wine photoshop launcher doesn't work"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by econobeing on 2006-12-09
i'm trying to create a launcher for photoshop (using wine of course)

right click desktop > create lancher...
^that type of launcher

i've made one for utorrent(also using wine), and i've made one for sunbird. but the one i made for photoshop does'nt... the command works in the terminal, but when i make a shortcut/launcher out of it, it does nothing when i try to execute it...

---

### Post by jacksaff on 2006-12-09
> **econobeing said:**
> i'm trying to create a launcher for photoshop (using wine of course)

right click desktop > create lancher...
^that type of launcher

i've made one for utorrent(also using wine), and i've made one for sunbird. but the one i made for photoshop does'nt... the command works in the terminal, but when i make a shortcut/launcher out of it, it does nothing when i try to execute it...

Does the target location have spaces in it's pathname? Try wine "path/to/photoshop.exe" if not.

---

### Post by econobeing on 2006-12-09
the command i'm using in my shortcut is:

wine ~/.wine/drive_c/Program\ Files/Adobe/Photoshop\ 7.0/Photoshop.exe

---

### Post by Afoot on 2006-12-09
If you want to do it like that, you have to put the full path name. ```
wine /home/user/and/then/path/to/photoshop/photoshop.exe
```

Programs running through wine usually run better if you 'are' in the directory of whatever program you want to run, so I'd recommend making a little .sh file that first cd:s to the directory, and then wine:s it. The shortcut itself just refers to that sh file.

This is how my sh file for World of Warcraft looks like:
```
cd /home/fredrik/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
wine WoW.exe

```

---

### Post by econobeing on 2006-12-09
i tried making a .sh file as follows:

> 
sudo cd /home/travis/.wine/drive_c/Program\ Files/Adobe/Photoshop/
sudo wine Photoshop.exe


but when i try to run it with a shortcut/launcher it gives me:

"there was an error launching the application
details: failed to execute child process "Desktop/ps.sh" (permission denied)"

---

### Post by Afoot on 2006-12-10
You shouldn't have sudo before the commands unless you don't have permissions to the file(s), which you by all probability do. And just as a side note, it won't work without terminal with sudo, you have to have gksudo: the graphical password asker. :)

**So, remove sudo** before the commands and it should work. If it doesn't, you haven't got the right permissions, in which case you could do something like this *(but remove sudo and try first)*:
```
sudo chmod 755 -R /home/youruser/.wine/
```

And, if that doesn't work either, then you don't have permissions to your sh file. So just change it with chmod.
```
man chmod
```

And just something you should remember, **never** run wine as root, so don't use sudo either.

---

