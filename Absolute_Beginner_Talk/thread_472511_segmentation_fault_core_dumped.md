---
title: "segmentation fault core dumped"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by drshrikant on 2007-06-13
ubuntu is the best thing that ever happened to my pc..
but am havin a serious problem with it all the time..
just in a few daz (4-5) after the install i keep gttin segmentation fault core dumped error..
then have to install it all again.. this is my 9th install so far..
even after bootin had got this msg after 1 install..
i'm using a low end machine with 20 mb sata disk 256 mb ram...
plz help.

---

### Post by bapoumba on 2007-06-13
Which application is giving core dumps?
Can you please launch it from a terminal and paste the complete output in here ?

---

### Post by drshrikant on 2007-06-13
get with add/remove prog and similar admin applications everytime...
for example right now... gettin it when tryin to install kubuntu desktop...

shrikant@shrikant-desktop:~$ sudo -i
Password:
root@shrikant-desktop:~# apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Segmentation fault (core dumped)
root@shrikant-desktop:~#

---

### Post by drshrikant on 2007-06-13
hey guys... 
                     no help????

---

### Post by bapoumba on 2007-06-14
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/57393]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/57393")
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/113424]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/113424")
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/16467]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/16467")
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/71028]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/71028")

Please have a look at these bug reports. They all have a different fixes, for different problems.

---

### Post by El Viejo Lobo on 2007-07-17
I got the same problem installing k3d on my laptop.
lobo@lobo-laptop:~$ k3d
Segmentation fault (core dumped)
lobo@lobo-laptop:~$ 

It did not pass   on my Desktop box on the same day installing in the same way.

Attached a screenshot of the terminal.

Is there a fix for this bug?

Bug: [https://bugs.launchpad.net/ubuntu/+source/k3d/+bug/118879](https://bugs.launchpad.net/ubuntu/+source/k3d/+bug/118879)

---

### Post by bapoumba on 2007-07-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/k3d/+bug/109116](https://bugs.launchpad.net/ubuntu/+source/k3d/+bug/109116) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I would say this one.

---

