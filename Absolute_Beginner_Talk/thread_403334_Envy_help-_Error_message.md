---
title: "Envy help- Error message"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Tim_06 on 2007-04-06
Hello.

Well Im trying to install Beryl, In one of the steps it tells me to Install Envy to obtain the correct drive software. 

Anyways, I save the Evy file to my desktop, when I double click to load it the package installer pops up, it does it's thing and then in bold letters an error says 

"Error: Dependency is not satisfiable: module-assistant"

What does this mean ?

What can I do and how do I do it ?

Cheers Tim

---

### Post by Najand on 2007-04-06
where did you get the package? Isn't it included in repositories?

---

### Post by Maestro23 on 2007-04-06
In terminal:

> sudo aptitude install module-assistant

---

### Post by Tim_06 on 2007-04-06
Hey I tried that code this is what I get.

tim@tim-desktop:~$ sudo -i
root@tim-desktop:~# sudo aptitude install module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "module-assistant"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
root@tim-desktop:~# 


Any help here ?  

I downloaded envy from this site [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)    i down loaded this one  envy_0.9.1-0ubuntu4_all.deb

Hope that helps

Cheers Tim

---

### Post by Maestro23 on 2007-04-06
It's in the repo's. Might need to enable extra repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by Najand on 2007-04-06
The package needs to install some other packages (dependencies):
debhelper, html2text, module-assistant, fakeroot, xserver-xorg-dev, dh-make
I think it can be ionstalled just simply by enabling Universe, Multiverse repositories and double clicking on your package again.

---

### Post by Tim_06 on 2007-04-06
Hey thanks for your help but Im really new at this. 

Can we please put this in to layman terms ?  Easy to understand steps ?

Thanks Tim

---

