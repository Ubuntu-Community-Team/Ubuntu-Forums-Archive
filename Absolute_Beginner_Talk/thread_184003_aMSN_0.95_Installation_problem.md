---
title: "aMSN 0.95 Installation problem"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by Souljah on 2006-05-29
Trying to install aMSN through synaptic package manager. It says I need to install **docker**, **galeon**, **galeon-common**, and **tcltls**. It says to mark all these packages for installation, so I do that. Then it gives me this problem:

> 
amsn:
 Depends: imlib1  but it is not installable
 Depends: sox but it is not going to be installed
 Depends: libpng10-0  but it is not installable


Basically says that the following packages have unresolved dependencies. So I have no idea how to install aMSN now :(. I try to install one of them, imlib, but then it says I need imlib-base which I search for and I cannot find. Totally clueless here.

---

### Post by Hellaxe on 2006-05-29
I think that's a problem with your sources.list.
Try another ones.
I´ve instaled on my Dapper test Vm and it was perfect.

---

### Post by Souljah on 2006-05-29
What do you mean with my sources.list. I'm actually rather new so I don't know how to try another one. I'm managed to install docker, galeon, galeon-common, and tcltls. However, the same problem is occuring. What do you recommend I do?

---

### Post by Souljah on 2006-05-29
A little update, I managed to get the imlib-base installed. I had to change my preferences to main, restricted, multiverse and universe for the binary versions. I have aMSN 0.94 installed and will try to upgrade now.

WOOHOO I troubleshoted my own problem :D

EDIT: I managed to install the 0.95 version on my own. Wow. Well this is a step to learning linux. :D

---

### Post by richbarna on 2006-05-29
[QUOTE=Souljah]A little update, I managed to get the imlib-base installed. I had to change my preferences to main, restricted, multiverse and universe for the binary versions. I have aMSN 0.94 installed and will try to upgrade now.

WOOHOO I troubleshoted my own problem :D

EDIT: I managed to install the 0.95 version on my own. Wow. Well this is a step to learning linux. :D[/QUOTE]

Well Done !!!!
We have all been there :)
That sweet sense of satisfaction when you finally work something out.
Keep learning and enjoy the experience.
Later you will be valuable in helping other new users when they have the same problems that you have encountered in the past.

---

