---
title: "Nothing will install..."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2008-03-04
The tittle says it all really everytime i try and install **anything** it says cannot find the software or whatever. Also whenever it asks to install most things, it wishes for me to put the ubuntu 7.10 i386 cd into the drive (which it was when i attempted to install all the software.) Some of the software in which i attempted to install would be adobe flash player, kismet, wine etc...

---

### Post by halitech on 2008-03-04
some software will only install from the repos so you need an internet connection as well as the cd. how are you trying to install and what do you get for error messages?

---

### Post by tennvolsmb on 2008-03-04
Well for adobe flash "can not find 'flashplugin-nonfree'", for kismet and wine i use the terminal and it says can not find the package.

---

### Post by glennric on 2008-03-04
Those packages are not on the cd.  To install flashplugin-nonfree make sure the gutsy-updates/multiverse repository is enabled.  For wine you will have to add the line
```
deb http://wine.budgetdedicated.com/apt gutsy main
```
to the file /etc/apt/sources.list
For kismet make sure that the gutsy-backports/universe repository is enabled.
You will have to have an internet connection as well.

---

### Post by Linux_Man on 2008-03-04
Make sure you have an active internet connection (Try typing "ping www.google.com" in the terminal and after a few seconds press Ctrl+C and see if all your packets got through) and you have all the repositories enabled.

---

### Post by tennvolsmb on 2008-03-04
How do i go about on checking if my repositories are enabled?

---

### Post by taurus on 2008-03-04
Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by tennvolsmb on 2008-03-04
Okay so none of them are like activated so how would i do that?

---

### Post by taurus on 2008-03-04
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close the gedit window.  

Then run

```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  And if you don't want it to ask you to insert the installer CD when you want to install something, put a # in front of the first line, cdrom, to comment it out.

---

