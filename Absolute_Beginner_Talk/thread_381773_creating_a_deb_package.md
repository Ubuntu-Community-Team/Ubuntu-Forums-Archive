---
title: "creating a deb package"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-03-11
Hi,

     I have found alot of interesting how-tos about installing various softwares. They are good but they are time-consuming to install them to multiple systems.

E.g. [http://www.ubuntuforums.org/showthread.php?t=156298&highlight=openfoam](http://www.ubuntuforums.org/showthread.php?t=156298&highlight=openfoam)

Is it possible that I can create a deb package and make sure the package runs all the steps needed after copying the necessary files to the appropriate folder?

Any change that it can automatically edit the bashrc files to update the changes?

I am new in terms of creating deb packages so need some help.

Thanks and appreciated.

---

### Post by IcarusR on 2007-03-11
If I understand you correctly, you are talking about installing from source or tarball onto several boxes.
 If so you can use [checkinstall]("http://asic-linux.com.mx/~izto/checkinstall/") 
This will create a .deb of your app as you install it.
You have to 
```
untar 
./configure
make  
```
as usual then
 ```
checkinstall -D 
```
which creates a .deb in the current directory for you to then install. 
```
dpkg -i /path/to/new/package.deb
```
This can also be uninstalled with Synaptic, should you wish to or 
```
dpkg -r /path/to/new/package.deb
```

Hope this helps.

---

### Post by in_flu_ence on 2007-03-11
but does this method only put the files into the appropriate folder? or it will do all necessary work like editing the .bashrc (which I doubt so). I think i need some tweak to ensure that post installation work can be done automatically?

---

### Post by IcarusR on 2007-03-11
No this will not edit individual files after install. But it will mean that you only have to do all the steps to manually install once. This therefore does go someway to achieving your goal !!!!!
Write a shell script to run dpkg then do your post install edits.

This is Linux not Windows things require some effort to get them to work how you want.

Exactly how many boxes are you doing these installs on ??

---

