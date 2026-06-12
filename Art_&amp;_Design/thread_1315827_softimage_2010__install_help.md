---
title: "softimage 2010  install help"
date: 2009-11-05
forum: Art &amp; Design
---

### Post by chinky005 on 2009-11-05
autodesk just recently released softimage 2010 and they have a linux version available and I've been trying to install it for quite some time now but it just dosn't seem to want to work. 

now it says the prefered os would be fedora core but I was wondering if there was anyway around that to install it on linux or is that realy the issue that is preventing me from installing it properly?

if anybody's installed it or knows how to install it please help me.

---

### Post by FiveSidedPoly on 2009-11-07
Bump: Hopefully someone can answer his question.
 
I really think you ought to try and get answers from Autodesk's site/forums.  *I *never installed Softimage on Linux, but the Softimage Mod Tool Kit was pretty straight forward.
 
Also I would make sure you're not trying to load a 64bit version onto a 32bit install of Ubuntu.

---

### Post by vinutux on 2009-11-07
All Autodesk linux products supported redhat/fedora paltform ....fedora/redhat using .rpm package instead of .deb

Use **[COLOR="SeaGreen"]alien[/COLOR]** for converting rpm to deb 

```
sudo apt-get install alien
```

after install ...  type this cammand 

```
alien -d [COLOR="Red"]/path2yourfile.rpm[/COLOR]
```


After converting is fininshed convereted .deb file is in your /home folder ..... Double click to install it............

---

### Post by chinky005 on 2009-11-08
> **vinutux said:**
> All Autodesk linux products supported redhat/fedora paltform ....fedora/redhat using .rpm package instead of .deb

Use **[COLOR="SeaGreen"]alien[/COLOR]** for converting rpm to deb 

```
sudo apt-get install alien
```

after install ...  type this cammand 

```
alien -d [COLOR="Red"]/path2yourfile.rpm[/COLOR]
```


After converting is fininshed convereted .deb file is in your /home folder ..... Double click to install it............

thanks man ganna try it out right now

---

### Post by chinky005 on 2009-11-09
> **vinutux said:**
> All Autodesk linux products supported redhat/fedora paltform ....fedora/redhat using .rpm package instead of .deb

Use **[COLOR="SeaGreen"]alien[/COLOR]** for converting rpm to deb 

```
sudo apt-get install alien
```

after install ...  type this cammand 

```
alien -d [COLOR="Red"]/path2yourfile.rpm[/COLOR]
```


After converting is fininshed convereted .deb file is in your /home folder ..... Double click to install it............

din't work....maybe it's because I don't know what I'm looking for but I don't see a .rpm file, I have some bidst_rpm.py files but it says must run as root to convert to db format (or you may use fakeroot).

---

### Post by vinutux on 2009-11-12
sudo is fakeroot............ use sudo before that cammand ```
sudo [COLOR="Red"]/pathtoyourfileRPM.py[/COLOR]
```

.Py is a python script i don't know how to convert this script to deb check out official documentations...........

---

### Post by Alaa2 on 2010-02-17
i have just downloaded softimage 2010 and its .tar.gz and when extracted i found that the files in it are .tar.gz too,.. so,... am new to ubuntu and linux,does anyone has any idea how to install these files ?

help is much appreciated

---

### Post by Alaa2 on 2010-02-19
ok never mind heres the answer,.... first get tcsh from synaptic and install it.

then run tcsh in the terminal,..just type in tcsh.

then simply run the "setup" file in the terminal and the installer begins.:D

---

### Post by iozk on 2010-05-18
ok for do the same i'll be install the alien too and for run the setup just type setup? for the softimage2011 is the same way?

---

### Post by iozk on 2010-05-18
how do you do for the licence manager works?

---

