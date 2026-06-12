---
title: "how to fix a broken package"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by waterspider on 2008-03-13
please can anybody help me to fix the broken here is what is displayed on terminal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  dvdisaster: Depends:  but it is not installable
E: Unmet dependencies. Try using -f.

---

### Post by OffAxis on 2008-03-13
literally, run the command that's listed:

```
sudo apt-get -f install
```

---

### Post by jan quark on 2008-03-13
you can also try
```

sudo dpkg --configure -a
```

---

### Post by waterspider on 2008-03-14
thnx alot........but whenever i tried to run the it gives me this output..............

 sudo apt-get -f install
[sudo] password for iceman:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  dvdisaster
Recommended packages:
  dvdisaster-doc
The following packages will be upgraded:
  dvdisaster
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/366kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2634 package `dvdisaster':
 `Depends' field, missing package name, or garbage where package name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by jan quark on 2008-03-14
the same with

```
sudo dpkg --configure -a
``` ???

---

### Post by waterspider on 2008-03-14
if i run the command it gives this replys 
sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2634 package `dvdisaster':
 `Depends' field, missing package name, or garbage where package name expected
iceman@braveheart:~$ sudo dpkg --configure -a
[sudo] password for iceman:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2634 package `dvdisaster':
 `Depends' field, missing package name, or garbage where package name expected

please help

---

### Post by wesley_of_course on 2008-03-14
In this thread ,[http://ubuntuforums.org/showthread.php?t=332671](http://ubuntuforums.org/showthread.php?t=332671) , 4th post they 
ran 'dpkg' directly on a .deb file to get a more verbose output . Not real sure how its done but post back and someone more knowledgeable than I will surely be able to help .  Let us know how it goes as I could learn how also .

---

