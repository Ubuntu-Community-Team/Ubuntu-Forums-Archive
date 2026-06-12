---
title: "[wta]install multimedia codecs"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-08-12
i want to install.........

libxine-extracodecs

i try few ways..........

install with adept.......

==========
Start Adept by choosing K Menu->System->Adept (Package Manager) from the Desktop menu system. 
 Select View->Manage Repositories in the Adept package manager window. 
To enable the Universe repository, find the repository line with the Universe Component, and right click the line and select Enable.
==========

cannot do~

then...i try........

============
penguin@penguin-desktop:~$ sudo apt -get install libxine-extracodecs
sudo: apt: command not found
penguin@penguin-desktop:~$
============

thats what i got.

emm...any one can help me?

---

### Post by Iarwain ben-adar on 2006-08-12
Hi, for the Adept way, what is it that you cannot do? (a bit more detailed)

and for the apt-get way => it's apt-get (written together ;-) )


Iarwain

---

### Post by bonjun on 2006-08-12
> **penguinKabuki said:**
> i want to install.........

libxine-extracodecs

i try few ways..........

install with adept.......

==========
Start Adept by choosing K Menu->System->Adept (Package Manager) from the Desktop menu system. 
 Select View->Manage Repositories in the Adept package manager window. 
To enable the Universe repository, find the repository line with the Universe Component, and right click the line and select Enable.
==========

cannot do~

then...i try........

============
penguin@penguin-desktop:~$ sudo apt -get install libxine-extracodecs
sudo: apt: command not found
penguin@penguin-desktop:~$
============

thats what i got.

emm...any one can help me?


it's the space between apt-get not apt -get

---

### Post by penguinKabuki on 2006-08-12
ooo...typo. :>

=======
penguin@penguin-desktop:~$ sudo apt-get install libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate
penguin@penguin-desktop:~$
=======

for adept.......
==========
i attach the print screen~~
==========

---

### Post by Iarwain ben-adar on 2006-08-12
You have to enable the multi-verse repo's i think :D

Adept => View => something with repositories (the second option)
and then you search for the multiverse repo's, and enable them ;-)


Iarwain

---

