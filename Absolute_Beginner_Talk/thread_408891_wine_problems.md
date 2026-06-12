---
title: "wine problems"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-04-13
OK, wine wasn't working (saying things like c:program files is not accesable) and stuff like that, and i did not even know where the wine folder was! But, then I learned it was a hidden folder so then I found it! i looked in their, and there is a c folder and a program files folder  and nothing is in their, or anywhere. Then I took my program, and put it in the system32, when i used wine "program" it said module not found. Does anyone know what is wrong?
all help is appreciated



-Sewercake

---

### Post by josephus on 2007-04-13
you shouldn't need to move your program into the wine directory in order to run it.

you should run 

```
winecfg
```

to properly configure wine first.  in the drives section you should make sure that c: is included and should point to ../drive_c  .  i think if you just use autodetect that is setup for you.

---

### Post by sewercake on 2007-04-13
it says this when I autodetect >  err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/media/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/media/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/home/sam'

so, ya.

---

### Post by josephus on 2007-04-13
weird.  

i'm not sure what that means -- try deleting the .wine directory and run winecfg again

btw which version of wine are you running?  the newest version is not in the standard repository ([http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb))

---

