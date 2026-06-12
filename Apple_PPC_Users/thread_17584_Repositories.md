---
title: "Repositories"
date: 2005-03-01
forum: Apple PPC Users
---

### Post by freemanen on 2005-03-01
My Repositories are incorrect. How do i change it to normal?

---

### Post by nemin on 2005-03-01
[QUOTE=freemanen]My Repositories are incorrect. How do i change it to normal?[/QUOTE]
Change /etc/apt/sources.list. When you only want "main" ubuntu packages, you can enter this:

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main


See: [http://ubuntuforums.org/archive/index.php/t-3305.html](http://ubuntuforums.org/archive/index.php/t-3305.html) for examples of other repositories you could enter :)

---

### Post by delltony on 2005-03-01
[QUOTE=freemanen]My Repositories are incorrect. How do i change it to normal?[/QUOTE]

go to a shell and type sudo gedit /etc/apt/sources.list
that will bring up your source list (repository file)
change it to the correct ones.

I use hoary so my repositories are different but if you do a search on the forum for extra repositories you will see a list of the correct ones for warty.  Hope this helps.
Just fix the ones in the file using # if needed. then save the file
Once saved then type sudo apt-get update to update the repositories
and then you can go from there. 

-tony-

---

### Post by bored2k on 2005-03-01
[QUOTE=delltony]go to a shell and type sudo gedit /etc/apt/sources.list
that will bring up your source list (repository file)
change it to the correct ones.

I use hoary so my repositories are different but if you do a search on the forum for extra repositories you will see a list of the correct ones for warty.  Hope this helps.
Just fix the ones in the file using # if needed. then save the file
Once saved then type sudo apt-get update to update the repositories
and then you can go from there. 

-tony-[/QUOTE]
 ## Main sources - Ubuntu Warty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Main sources - Ubuntu Warty security updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

## Universe sources - Ubuntu Warty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

## Multiverse sources - Ubuntu Warty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse 

## Java sources - Ubuntu Warty
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java 

## Backport sources - Ubuntu Warty
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports main universe m
ultiverse restricted 
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-extras main universe mult
iverse restricted 

## Marillat's Sources (MPlayer, w32 video codecs, etc.)
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main  
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main  
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

u will need to remove the # from Marillat's ones to use them.

---

### Post by BeTa on 2005-03-01
For the marillat's repository, it's only for i386 & amd64. just take a look at his main page [ [ftp://ftp.nerim.net/debian-marillat/index.html](ftp://ftp.nerim.net/debian-marillat/index.html) ], it explains things for PPC users. In any case, you may be able to use the deb-src repository... ;c)

have fun ! :c)

---

### Post by freemanen on 2005-03-01
It didn't work. I copied the text to /etc/apt/sources.list.

---

### Post by nemin on 2005-03-28
[QUOTE=freemanen]It didn't work. I copied the text to /etc/apt/sources.list.[/QUOTE]
What do you mean didn't work? Did you get an error message? Did you do apt-get update?

---

