---
title: "Installing RPM files...?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by ayq on 2006-08-20
I've searched around the forums a little bit and I couldn't find anything regarding this but uhh...

I just recently downloaded a program that came as a .RPM file and I have no idea what I'm supposed to do with it. All of the programs that I've been installing have all been with synaptics and automatix so I don't have any expierience installing anything manualy.

That is all.

---

### Post by sethmahoney on 2006-08-20
If its not in synaptic, you should try to download a .deb file to install, not an rpm.  debs can be installed by typing 

sudo dpkg -i myfile.deb

in a terminal (replacing myfile with the actual filename).  If you can only get an rpm (what is it you're trying to install, by the way?), you can try to install it with alien.

---

### Post by Klaidas on 2006-08-20
RPM is not the format Ubuntu uses, but you could use a program called "alien" to convert RPM to DEB.
Hoowever, I recommend reading aysiu's guide about installing stuff on Ubuntu:  [http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)

---

### Post by crackseller on 2006-08-20
Get alien ...
```
sudo apt-get install alien
```
then convert the package via
```
alien -d <packagename>.rpm
```
... and then you can install it the usual way. Or you can just convert+install it with ...
```
alien -di <packagename>.rpm
```

Note: Converting .rpm to .deb does not always succeed, therefor, if you can, get the package as a .deb file or compile the source yourself.

---

### Post by kinematic on 2006-08-20
you people are fast with replying ;)

---

### Post by baldy1324 on 2006-08-20
well first .rpm is not for ubuntu and debian distributions but you can get it to work. first before you download a .rpm file (a package for redhat based distros) check to make sure there is a not  a .deb (a debian package that works in ubuntu/debian) and it is not in synaptic.

now if none of that exists here is how to install the rpm file. if you download the rpm to the desktop do this.
```
sudo apt-get install alien
alien ./Desktop/*.rpm
dpkg -i ./Desktop*.deb

```

what this will do is first install alien and its dependencies, the run alien to convert the rpm package to a debian package, and then install the debian package on your system
hope that helped

---

### Post by ayq on 2006-08-20
Thanks for the help. This is actualy what I was trying to install:

[http://sourceforge.net/project/showfiles.php?group_id=1369&package_id=1351](http://sourceforge.net/project/showfiles.php?group_id=1369&package_id=1351)

Now I notice that the .tar.gz has everything I need (I think, I haven't actualy tried it out yet)

I was just trying to download an example python game and it said that it requires Numerical Python as well as PyGame so I went looking.

---

