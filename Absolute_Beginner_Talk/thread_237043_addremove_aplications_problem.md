---
title: "add/remove aplications problem"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by inmate#001 on 2006-08-15
the add/remove applications program is not working corectley i have added the extra repositories and it does not have any of those programs listed and everytime i start it it says the database is out of date and it needs to update it can sombody help me with this problem

---

### Post by shoot2kill on 2006-08-15
yes, try opening terminal and typing
> sudo aptitude update

just out of interest, what are you trying to install, because an aptitude install might be easier and quicker...

---

### Post by geokok1981 on 2006-08-15
why aptitude and not apt?
I had the same problem when I messed my sources and had to replace the sources file with a new one.
But after a couple of times (a restart maybe as well but not sure) it worked fine.
Any chance u have messed the sources file?To restore the file u can use the text produced here:
[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by xpod on 2006-08-15
Aptitude as apose to apt-get apparently removes all of the packages that it installs unlike apt-get that supposedly leaves a lot of dependancys behind when you uninstall with it...

Im sure thats right but feel free to correct me if im wrong

---

### Post by geokok1981 on 2006-08-15
Yeah but I was told u shouldn't mix those two or u might mess your system. So, having in mind that things that are left behind don't really take any space nor they degrade system performance why not 
stick with apt-get and keep your calmness and tranquility?

---

### Post by auzzie on 2008-01-11
> **shoot2kill said:**
> yes, try opening terminal and typing


just out of interest, what are you trying to install, because an aptitude install might be easier and quicker...

Well i am having the same problems, tried your solution and there is no difference, i havent messed with anything it is a fresh install

---

