---
title: "I have two hard drives one ubuntu one with xp"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-04-24
I have xp on one drive and ubuntu on another.  I do not have them master or slave I have been unpluging etc.  I would like to know if there is an how to on duel booting when you already have both os's on two different drives.  Is this possible/

---

### Post by Drifter on 2007-04-24
anyone please help

---

### Post by click4851 on 2007-04-24
yes it is possible, when I loaded edgy (6.10) on my master hardrive, it acknowledged my other hardrive with windows and GRUB  listed an option at the bottom of the boot screen for WinXP, which i use time to time mainly for games I play. I must admit I have never configured it after the fact, but it is possible. Maybe using a SuperGRUB disk?

---

### Post by Drifter on 2007-04-24
what is a super grub disk and where to get it

---

### Post by louieb on 2007-04-24
Here is an easy way. 
Plug ubuntu drive in as master
Plug XP drive in as slave
Add the following to /boot/grub/menu.lst
to edit press Alt+F2
```
gksudo gedit /boot/grub/menu.lst
```
```
title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
      boot

```[URL="http://louboldt.com/ilinuxgrub.htm"]more on this
[/URL] explains what to do in greater detail

---

### Post by confused57 on 2007-04-24
Lou, nice website...just added it to my Bookmarks.   Thanks.

---

### Post by ginnie6 on 2007-04-24
what I have is installed XP is on my master and I put Ubuntu on the slave.......ubuntu is the first boot option and xp is last.

---

### Post by Drifter on 2007-04-25
I now have both working fine thanks for your help.

---

### Post by Drifter on 2007-04-25
Great site there louie I also saved it as fav. thanks

---

### Post by louieb on 2007-04-26
Thanks for the complements.

---

