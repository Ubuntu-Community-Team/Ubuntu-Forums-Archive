---
title: "java runtime problem"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-11-23
when i run this command it cant find the package
does anyone know if theres a different package name

:~$ sudo apt-get install sun-j2rel.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2rel.5
becky@ubuntu:~$

---

### Post by odin on 2005-11-23
have you tried with apt-cache search?

In case you dont know what I'm talking about it'd be someting like this:

sudo apt-get update
sudo apt-cache search java (instead of java you can write sun or j2re just to try)

With that you'll get a list of all programs related to what you wrote so you can see if the name of the package is different.But as far as I can remember either I dont have my repos up to date or j2re1.5 is not available yet only j2re1.4.

---

### Post by odin on 2005-11-23
sorry I was wrong.I guess you dont have some repos in your lost that you need but I dont know exactly which one you need for this package.

go to this link [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) and see how to update your /etc/apt/sources.list and sure it will work with:

sudo apt-get update
sudo apt-get install sun-j2re1.5

Sorry for the mistake and hope this time I'm right :D

---

### Post by grim918 on 2005-11-23
when i run this command i get this error. does anyone know how i can fix it

:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2re1.5 has no installation candidate

---

### Post by d1337 on 2005-11-23
Do you have your repositories straight?  Odin's link should help you out.

d1337

---

### Post by asksubbu on 2005-11-24
There is an excellent section on JRE/JRK installation as part of 5.10 starter guide (Breezy), go by the steps, it works like charm.

System > Help > Ubuntu 5.10 Starter Guide > Applications > Java

---

### Post by fuscia on 2005-11-24
you could try using automatix. [http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix)
i installed a bunch of stuff using it, including java runtime. when i installed opera with it, it was the first time i did without getting any missing lib errors.

---

