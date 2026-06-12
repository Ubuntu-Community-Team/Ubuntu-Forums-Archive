---
title: "help to install stuff"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-03-07
Hi, i am absolutly new to Ubuntu.
When i tryed to download Wine or a theme from [http://www.gnome-look.org/](http://www.gnome-look.org/) i can't install it. in windows i just had to push, install. How do i do it in ubunu

---

### Post by melancholeric on 2007-03-07
sudo apt-get install wine

as for themes:

Desktop -> Preferences -> Theme; drag and drop the .tar.gz file there. Should work.

Or, if there's an "Art Manager" item under "Preferences", that'll get more themes from art.gnome.org.

---

### Post by ajmannen on 2007-03-07
Ok, but how do i run sudo apt-get install wine?

---

### Post by melancholeric on 2007-03-07
Applications -> Accessories -> Terminal

---

### Post by aktiwers on 2007-03-07
remember to run: winecfg
when the install is done.

---

### Post by Perfect Storm on 2007-03-07
For theme/eyecandy check this: [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

about wine, it's a good idea to add WineHQ ubuntu source in your repo to get the latest.

---

### Post by ajmannen on 2007-03-07
when trying to install wine i get this: 
andreas@Jacobsen:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
:confused:

And, can i install limewire in ubuntu?

---

### Post by Perfect Storm on 2007-03-07
```
cat /etc/apt/sources.list
```


Yes you can install limewire on Linux/Ubuntu, but it also require Java to do so.

---

### Post by aktiwers on 2007-03-07
I would not recomment you to use wine. Not that it isnt good to run programs that there are no alternatives to, but its always better to use a linux app. It just runs better.

I see many people wanting wine because they simply dont know the linux alternative to the program they are seeking. For an example I have seen people wanting to run MSN through wine only because they didnt know about Gaim or aMSN (or others).

Always try finding the alternative first is my suggestion. 


If you havent already seen it, you should have a look at automatix2 which will install a lot of software for you automatically. Including Wine, Java, a limewire program, flash, media codex and lots more.

Check it out:
[www.getautomatix.com]("http://www.getautomatix.com") 

And good luck.

EDIT:
Automatix webpage seam to be down now.. check back later.. awesome app!

---

