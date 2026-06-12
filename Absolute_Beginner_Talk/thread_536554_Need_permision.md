---
title: "Need permision"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Bout to Snap on 2007-08-27
Need to copy some files to the game folder cause of a game update (patch) says it only needs to be in the directory of the game itself however i need permision to do so anyone have any idea's?

---

### Post by mevets on 2007-08-27
Hit Alt+F2
> 
gksudo nautilus


---

### Post by Bout to Snap on 2007-08-27
> **mevets said:**
> Hit Alt+F2

ooh snap! nice answer and quick to ...thanks man

---

### Post by s[_]spect on 2007-08-27
Open terminal and type:
sudo chmod 777 <directoryyouwant perms to>
Note this gives read write and execute permission to all users for this folder..
type man chmod for more detail

---

### Post by Bout to Snap on 2007-08-27
> **'s[_]spect said:**
> Open terminal and type:
sudo chmod 777 <directoryyouwant perms to>
Note this gives read write and execute permission to all users for this folder..
type man chmod for more detail

thanks man that was very helpfull also.

---

### Post by jw5801 on 2007-08-27
Or just ```
sudo mv */directory/file* /game/*file*
```
Be careful with nautilus as root, you can do some nasty things that way :p

EDIT: [The reason we don't like using Nautilus as root](http://ubuntuforums.org/showthread.php?t=536678)

---

### Post by Bout to Snap on 2007-08-28
> **jw5801 said:**
> Or just ```
sudo mv */directory/file* /game/*file*
```
Be careful with nautilus as root, you can do some nasty things that way :p

EDIT: [The reason we don't like using Nautilus as root](http://ubuntuforums.org/showthread.php?t=536678)

Yeah i know, I just had to copy a game update. which while i was in there i deleted a few unwanted games that i had downloaded and installed other than that im good to go, Thanks for the help guys.

---

