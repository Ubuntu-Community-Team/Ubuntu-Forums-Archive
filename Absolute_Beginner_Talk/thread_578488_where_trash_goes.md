---
title: "where trash goes ?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-10-17
Yeah, I just deleted some rather large files on an ntfs-3g partition,and nothing has changed in the system monitor,I still get 79% used on that partition ! I have looked in home/.trash
but nothing shows up. Any help ? :confused:

---

### Post by 1337455 10534 on 2007-10-17
Try getting a shredder. I'm sure there is an obscure UNIX command that runs 0 byte strings through a directrory. I read about ti somewhere/

---

### Post by shen-an-doah on 2007-10-17
> **Drakkor said:**
> Yeah, I just deleted some rather large files on an ntfs-3g partition,and nothing has changed in the system monitor,I still get 79% used on that partition ! I have looked in home/.trash
but nothing shows up. Any help ? :confused:

Usually it'll be in the top level of the partition. So if your disk is C:\ in Windows, then it'll be in C:\.Trash. Or if it's mounted as something like /media/sda1/ on Ubuntu, then it'll be in /media/sda1/.Trash.

Sometimes the folder will have a suffix of your username on it. Like mine ends up in .Trash-andy

---

### Post by gOLdenHaWK3D on 2007-10-17
> **Drakkor said:**
> Yeah, I just deleted some rather large files on an ntfs-3g partition,and nothing has changed in the system monitor,I still get 79% used on that partition ! I have looked in home/.trash
but nothing shows up. Any help ? :confused:

Dont worry, Just press Ctrl+H key to show the Hidden files. 
Now goto your NTFS Partition.
You can see the .Trash folder on that Drive now. Delete that folder, by pressing Shift+Delete keys.
Its gone forever now :)

---

### Post by Dr Small on 2007-10-17
I always press Shift + Delete these days.. saves me time from empting a trash can :p

Dr Small

---

### Post by aktiwers on 2007-10-17
If you where root while deleting, remember to check Roots .trash folder(s). :)

---

### Post by shen-an-doah on 2007-10-17
> **gOLdenHaWK3D said:**
> 
Its gone forever now :)

Until you delete more files on that partition. Then it's back...

---

### Post by Drakkor on 2007-10-17
Yeah,Thanks guys, got them deleted ! :) Going solo Gustsy now,and moving stuff around, I already formated my C:\ drive to ext3, and am going to do the same with this other partition.......no more ntfs........no more windows !!        :)

---

### Post by gOLdenHaWK3D on 2007-10-17
> **shen-an-doah said:**
> Until you delete more files on that partition. Then it's back...

:P

---

### Post by Drakkor on 2007-10-17
Well , I just deleted the whole partition,lol,and made it ext3, more storage ! :)

---

