---
title: "cant open apt"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-26
Hello i just tried to install automatix2 by following the instructions on their website. evrything went well untill i typed the command: sudo apt-get install automatix2.
then it said in the terminal could not find the package automatix2.
so i typed the command sudo apt-update again and then i got this in the terminal

armcandy@armcandy-desktop:~$ sudo apt-get update
E: Type '&#8220;deb' is not known on line 35 in source list /etc/apt/sources.list
armcandy@armcandy-desktop:~$ 

and when i try to open adept manager it just starts to load but wont open.
i am really confused and some help would be nice.

---

### Post by taurus on 2007-02-26
Remove the ' (at the beginning and end) from line 35 of your /etc/apt/source.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by solar george on 2007-02-26
> “deb
Remove the quotation marks from you sources.list and retry.

---

### Post by hempa on 2007-02-26
Thanks now everything works and i have installed Automatix:)

---

### Post by BeauBobbitt on 2007-05-30
I have the same problem after trying to load Automatax2.  I am too new to the world of UMBUNTU to fully understand your fix.  I got th elist but do not know what question marks to eliminate or how to save the list back with the changes.   Now, the automatic updated WILL NOT WORK.   Shows same error.

Thanks in advance but without the update feature I am in a bit of a fix.

---

### Post by taurus on 2007-05-30
> **BeauBobbitt said:**
> I have the same problem after trying to load Automatax2.  I am too new to the world of UMBUNTU to fully understand your fix.  I got th elist but do not know what question marks to eliminate or how to save the list back with the changes.   Now, the automatic updated WILL NOT WORK.   Shows same error.

Thanks in advance but without the update feature I am in a bit of a fix.

Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Outrunner on 2007-05-30
You don't remove question marks, you have to remove the *quotation* marks -> "

---

### Post by BeauBobbitt on 2007-05-30
That did it.   Since I am trying to learn at warp speed and don't like fixing things without understanding them can you refer me to where I can read what that list I edited is and its function?

Thanks so much - built Z80 computer in the 70's and now I feel like that same learning curve is on again!

Love LINUX.

:p

---

