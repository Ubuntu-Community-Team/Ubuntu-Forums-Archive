---
title: "How to install apps from cd?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by jimmyt on 2006-06-15
I'm lost. 
I've been using win/dos pcs since 1984. 
I'm trying to coax some life out of 10 old pcs in our school by running  Ubuntu - they were running win98. 
They are not connected to the internet and are not networked. they are standalone computers. I have managed to install Ubuntu (alternate) 6.06 using  a Desktop CD I dl'ed from here.
I want to install other apps from the CD but have no idea how. 

Inkscape and Scribus are the apps.

Any help appreciated.

---

### Post by aysiu on 2006-06-15
I don't think Inkscape and Scribus are on the CD.

---

### Post by bruce89 on 2006-06-15
No, but they would be on a DVD version if it was available.

---

### Post by jimmyt on 2006-06-15
They are mentioned on the list of packages
[http://packages.ubuntu.com/dapper/graphics/]("http://packages.ubuntu.com/dapper/graphics/")
and I assumed they were on the Cd.

---

### Post by catlett on 2006-06-15
If you have one computer with internet access. You can download the applications here.  [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)  Then copy the packages to a cd and use the cd to install them to the other computers.

Edit: Didn't see your post. That is a list of available packages from the Ubuntu repository. There are thousands of them. Ubuntu keeps to a 1 cd install, This limits the number of packages it can load on install. The rest of the packages are available via synaptic package manager for download and install throught the internet.
If you follow the links where you are and then scroll down you will see the download box. Download and make your own cd.

P.S. If you are comfortable with ubuntu/linux this would be the best way to create a cd with ubuntu aplications after install. [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by bruce89 on 2006-06-15
The CD is only a small subset of the packages.  The CD has about 1 000 packages, where the internet repository has 19 029 packages.

---

### Post by aysiu on 2006-06-15
Most packages listed in [http://packages.ubuntu.com](http://packages.ubuntu.com) are not on the CD.

Those draw from huge online repositories... much bigger than 700 MB.

---

### Post by jimmyt on 2006-06-15
thank you Catlett, I'll try hat route.

---

### Post by aysiu on 2006-06-15
You might also want to look into [Ubuntu Plus](http://www.ubuntuforums.org/showthread.php?t=183933)--I'm not sure if it has Scribus and Inkscape, though.

---

### Post by jimmyt on 2006-06-16
OK apps burned to CD.
Using the package manager, I tried Inkscape then Banshee.

Inkscape--
Error: Dependency is not satisfiable: libglibmm-2.4-1c2a
Banshee--
Error: Dependency is not satisfiable: mono-jit

---

### Post by pelago on 2006-06-16
Oh dear, you'll probably need to burn some dependencies to CD too, and then dependencies of dependencies. You can use synaptic to see dependencies of different packages. If you tick to install a package in synaptic it will tell you which other packages it will require. You'll need to download and install them too.

---

### Post by pellgarlic on 2006-06-17
FYI: a list of packages that come by default with dapper can be found here: 

[http://packages.ubuntu.com/dapper/allpackages.en.txt.gz](http://packages.ubuntu.com/dapper/allpackages.en.txt.gz)

(results are, as stated, acquired using "dpkg -l" on fresh install of dapper)

---

