---
title: "How to apply  a patch?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by aabento on 2006-12-24
I am using Ubuntu version 6.10 and I would like to work with the 
SchoolBell. I installed version 1.2.4 through the Synaptic Manager 
and I can see that the SchoolBell is working if I go to 

[http://localhost:7180](http://localhost:7180)

When I try to create users, groups,  modify passwords, etc, 
appears me an error 

"It system error occurred". 

I *googled* and I found the problem. The Ubuntu has a Bug in the 
"compilation" of the Scoolbell and is necessary to apply a patch. 
This is my problem. How to apply  a patch? :confused:  

Patch is in 

[http://patches.ubuntu.com/s/schoolbell/schoolbell_1.2.4-2ubuntu1.patch](http://patches.ubuntu.com/s/schoolbell/schoolbell_1.2.4-2ubuntu1.patch) 

Please say me as to apply one patch step by  step because 
it is the first time that I will try to make this. :confused: 

Thank you.:)

---

### Post by pay on 2006-12-24
Well you need to apply the patch to the source code. Usually like```
patch -p0 <schoolbell_1.2.4-2ubuntu1.patch
```but sometimes it's -p1.. I can't find the source code so I can't really help you much more than to tell you to download the source code, patch it, type "./configure" and then "make" and then "sudo make install"

---

### Post by Jussi Kukkonen on 2006-12-24
That patch modifies the debian packaging (the installer, so to speak), so you will have to learn not only how to patch, but how to compile and package debian packages.

If all goes well you should just have to get the source, patch like pay told you and then run "dpkg-buildpackage -rfakeroot -uc -us" in the source directory. You should get installable .deb-files in the parent dir. It's not always that easy though.

Before you can dpkg-buildpackage, you'll need to install the needed programs, though. At least the "build-essential" package.

---

### Post by pay on 2006-12-24
If using dpkg-build, you might aswell just```
sudo aptitude install build-essential
sudo apt-get build-dep schoolbell # if you have the src repo
apt-get source schoolbell
cd schoolbell*
wget http://patches.ubuntu.com/s/schoolbell/schoolbell_1.2.4-2ubuntu1.patch
patch -p0 <schoolbell_1.2.4-2ubuntu1.patch
cd
sudo apt-get --build source schoolbell
sudo dpkg -i schoolbell*.deb
```But like Jussi Kukkonen Jussi said, there can be complications so it is recommened to learn how to compile manually.

---

