---
title: "Opera install problem.."
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by champ_rock on 2006-07-07
hi

i am trying to install opera but am not able to do so... can u please tell whats going wrong...

> root@ubuntu:/home/ubuntu/epiphany-1.8.5# apt-get install opera
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  opera: Depends: xlib6g (>= 3.3.6) but it is not installable or
                  xlibs but it is not installable
E: Broken packages


---

### Post by Colonel Kilkenny on 2006-07-07
There are many threads about this problem. Try using search.
What you need to do for example is to get xlibs-package from breezy repositories. There are also other ways, but the search will help.

---

### Post by sumitsen on 2006-07-07
Hi,

First update the repository.
visit the link: [http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)

Do exactly the same as it says in that link to edit your sources.list file

then run the commands in the terminal:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install module-assistant build-essential

sudo apt-get install opera

This will perhaps resolve your package dependencies problem.

Dont forget to update the sources.list using the above mentioned link.

cheers, sumit

---

### Post by FredB on 2006-07-07
> 
sudo apt-get install build-essential
sudo apt-get install module-assistant build-essential

Why ? Do you want to intall make, gcc and all the other packages related to build-essential ?

And also : never ever use root account on Ubuntu (or any other distro) : it is very dangerous. Sudo is made for temporary root rights using.

---

### Post by Kobalt on 2006-07-07
> **FredB said:**
> Why ? Do you want to intall make, gcc and all the other packages related to build-essential ?

And also : never ever use root account on Ubuntu (or any other distro) : it is very dangerous. Sudo is made for temporary root rights using.

Build-essential is a very useful package, one of the first I installed actually. And also : there is no "root account" in Ubuntu...

IMHO, sumitsen gave good advices...

---

### Post by champ_rock on 2006-07-07
well what exactly wil this Build essential do??

---

### Post by hasimir44 on 2006-07-13
1. there actually is a root account, which you can access by:

sudo su

2. the 'build-essential' pkg installs pkgs for compiling and installing other packages manually and is quite useful if you know how to use them. it installs the following: 

  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libstdc++6-4.0-dev make

3. following the above directions resolved the above error and i was able to install opera. now i can surf at work without being logged (using xming, putty, and opera from my home pc..). 

xubuntu is awesome. just had to say that :)

hasimir44

---

