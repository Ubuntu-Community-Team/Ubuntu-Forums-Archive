---
title: "Change the location of a folder?"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Wiebelhaus on 2007-11-21
Is there a simple way to change the location of say Music folder? which is /home/user/music to say sdb1/yadda/yadda/music?

Thanks.

in the pic I can't figure out a way to change that location.

---

### Post by banewman on 2007-11-21
The easy way is to use nautilus to open /home/user and  sdb1/yadda/yadda - you can have them both open on the same workspace - then right click the music folder in /home/user and select cut from the drop down menu, then right click in sdb1/yadda/yadda  and select paste. :)

---

### Post by Wiebelhaus on 2007-11-21
> **banewman said:**
> The easy way is to use nautilus to open /home/user and  sdb1/yadda/yadda - you can have them both open on the same workspace - then right click the music folder in /home/user and select cut from the drop down menu, then right click in sdb1/yadda/yadda  and select paste. :)

Is this guy being funny? that doesn't sound logical , can someone confirm that please , thanks.

Just to clarify just in case I wasn't clear , I need to simply re-route my music , pictures , video's , document folder links/shortcuts to a secondary ext 3 storage hard drive that contains a truck load data.

---

### Post by daimaru on 2007-11-21
> **sx66gns said:**
> Is this guy being funny? that doesn't sound logical , can someone confirm that please , thanks.

you do want to move your folder right? its the normal ctrl+x ctrl+v method, so either do as he said or hold down shift while dragging to the other folder which does the same.
EDIT: but if you have music programs  watching folders for music in that location you will have to change that in the settings of that program.

---

### Post by Wiebelhaus on 2007-11-21
No , I don't want to move or copy data , I need to re-route the system shortcuts to another location on a secondary ext3 HDD , so that when I open "Music" it actually opens the location on "/sdb1/yadda/yadda/music."

---

### Post by daimaru on 2007-11-21
ah ok then you can create a symbolic link to that location. that should work.

---

### Post by Wiebelhaus on 2007-11-21
Unfortunately , symbolic link only works on the desktop.

Maybe I'm asking the wrong question , How do I edit folder properties?

---

### Post by daimaru on 2007-11-21
so all you want is to have a shortcut to the music folder on some other hardisk in your /home/music location right. open up your home folder and your yaddda disk.  select the folder you want from the yadda hardisk (/mnt/sdb1/yadda/yadda/music) hold down ctrl+shift and drag it to your home folder. this creates a shortcut to that location so if you click it it opens that location. is that what you wanted. sry i really am trying to help just don't really know if this is what you wanted. :)

EDIT:you can rename the folder afterwards to music if it wasnt called the same on yadda disk

---

### Post by smartbei on 2007-11-21
No, a symbolic link definately works not only on the desktop. Try this (After deleting the Music folder from /home/user):
```

ln -s /sdb1/yadda/yadda/music Music

```
That will create a link called Music in your home directory pointing to /sdb1/yadda/yadda/music.

---

### Post by Wiebelhaus on 2007-11-21
> **smartbei said:**
> No, a symbolic link definately works not only on the desktop. Try this (After deleting the Music folder from /home/user):
```

ln -s /sdb1/yadda/yadda/music Music

```
That will create a link called Music in your home directory pointing to /sdb1/yadda/yadda/music.


```
ln -s /sdb1/yadda/yadda/music /home/user/Music
```


thanks , will this also function with shortcuts such as Places/Music?

thanks again.

---

### Post by Wiebelhaus on 2007-11-21
> **daimaru said:**
> so all you want is to have a shortcut to the music folder on some other hardisk in your /home/music location right. open up your home folder and your yaddda disk.  select the folder you want from the yadda hardisk (/mnt/sdb1/yadda/yadda/music) hold down ctrl+shift and drag it to your home folder. this creates a shortcut to that location so if you click it it opens that location. is that what you wanted. sry i really am trying to help just don't really know if this is what you wanted. :)

EDIT:you can rename the folder afterwards to music if it wasnt called the same on yadda disk

Thanks for the help.

---

