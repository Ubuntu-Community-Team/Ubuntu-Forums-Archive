---
title: "Installing Java"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2008-03-08
I downloaded Frostwire, and figured out I needed Java. Is there anywhere I can get a Java deb?

---

### Post by taurus on 2008-03-08
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by jken146 on 2008-03-08
It's in the repositories.  The package is **sun-java6-jre**

Either install it in Add/Remove or Synaptic or by typing ```
sudo aptitude install sun-java6-jre
```

---

### Post by x05 on 2008-03-08
Be careful in the Gnutella network running Linux. Someone hacked me and changed my password, took me a week to get it all straightened out. Just warning you.

---

### Post by gustasonfrever on 2008-03-08
I did that and I got this

norgren@norgren-laptop:~$ sudo apt-get update
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Fetched 1B in 1s (1B/s)
Reading package lists... Done
norgren@norgren-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin
norgren@norgren-laptop:~$ java -version
The program 'java' can be found in the following packages:
 * cacao (You will have to enable component called 'universe')
 * j2re1.4 (You will have to enable component called 'multiverse')
 * kaffe (You will have to enable component called 'universe')
 * jamvm (You will have to enable component called 'universe')
 * java-gcj-compat
 * gij-4.1 (You will have to enable component called 'universe')
 * gij-4.2
 * sablevm (You will have to enable component called 'universe')
Try: sudo apt-get install <selected package>
bash: java: command not found
norgren@norgren-laptop:~$ sudo aptitude install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "sun-java6-jre"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading tate information... Done
Reading extended state information  
Initializing package states... Done
Building tag database... Done      
norgren@norgren-laptop:~$ 

Does that mean it has succesfully been installed? After I did that I tried opening frostwire and it still won't open

---

### Post by jan quark on 2008-03-08
you have to enable the software sources 

go to system > administration > software sources 

and check everything except source code and cd

then run this again
```

sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by cbiere on 2008-03-08
> **x05 said:**
> Be careful in the Gnutella network running Linux. Someone hacked me and changed my password, took me a week to get it all straightened out. Just warning you.

Yeah really? Would you care to explain how you deduced that you were hacked because of using the Gnutella network? Could you enlight us and explain which vulnerability was used?

I find it very interesting that someone with a SCAM link in his signature is such a helpful fella.

---

