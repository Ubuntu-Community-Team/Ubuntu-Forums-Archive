---
title: "how to install Kiba-dock *full on linux noob*"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by gutsynoob1 on 2007-11-13
hi, i would like to install kiba dock, im a full on linux noob and wouldnt no where to start, 

thanks

---

### Post by overdrank on 2007-11-13
> **gutsynoob1 said:**
> hi, i would like to install kiba dock, im a full on linux noob and wouldnt no where to start, 

thanks

HI and welcome you can download it here
[http://3v1n0.tuxfamily.org/apt-repository/dists/edgy/beryl-svn/](http://3v1n0.tuxfamily.org/apt-repository/dists/edgy/beryl-svn/)
It worked for me on gutsy. Good luck!

---

### Post by gutsynoob1 on 2007-11-14
thanks, i downloaded the links in the picture and they opened with package installer but it said "Error: Dependency is not satisfiable: libakamaru0"

what should i do,

thanks

---

### Post by SomeGuyDude on 2007-11-14
> **gutsynoob1 said:**
> thanks, i downloaded the links in the picture and they opened with package installer but it said "Error: Dependency is not satisfiable: libakamaru0"

what should i do,

thanks

Scroll up on the page, there's another package to download called "libakamaru0". Install that, then try again.

EDIT: Nevermind. I tried myself and when I tried to install Kiba-dock it said I needed Kiba-Plugins. When I tried to install Kiba-Plugins it said I needed Kiba-Dock. Awesome circular requirements!

---

### Post by CatKiller on 2007-11-14
> **SomeGuyDude said:**
> EDIT: Nevermind. I tried myself and when I tried to install Kiba-dock it said I needed Kiba-Plugins. When I tried to install Kiba-Plugins it said I needed Kiba-Dock. Awesome circular requirements!

You can do both at the same time with, for example ```
dpkg -i kibadock-whatever.deb kibaplugins-whatever.deb
```

---

### Post by gutsynoob1 on 2007-11-14
yeah, the above just happened to me :(

i really want this dock to be working, it looks great


> You can do both at the same time with, for example
Code:

dpkg -i kibadock-whatever.deb kibaplugins-whatever.deb

what does this mean? do i type it into to termanal, i did and it said this requires superuser privilages

---

### Post by CatKiller on 2007-11-14
> **gutsynoob1 said:**
> what does this mean? do i type it into to termanal, i did and it said this requires superuser privilages

You're quite right. I should have said. Use **sudo** to get root privileges: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I didn't say what the files would be called because I don't know - I'm using the Avant Window Navigator these days - but you'd put whatever the names are for the .deb files you want to install where I've put the "whatever" files. dpkg is a program for de-packaging .deb files, and the -i option means that you want to install them.

So put a sudo in front of the command, and replace the whatevers with what your files are called.

Oh and yes, this is input at the terminal. Also, you'll need to have changed directory to where you've saved the files, so if they're on your Desktop, for example, you'd do ```
cd Desktop
sudo dpkg -i kibadock-whatever.deb kibaplugins-whatever.deb
```

---

### Post by gutsynoob1 on 2007-11-14
:| i pretty much dont understand a word you just typed....

isnt there like a self installer or something, this makes me wanna go back to windows, all this termanal stuff

---

### Post by CatKiller on 2007-11-14
Normally software install isn't complicated at all - you type in your password, find the software in a list and click the box that says you want to install it. Easy.

But because you want to install something that's not in the repositories, you need to get the program installed yourself. Read that wiki page, and it will explain the root user to you (by default you can only write to files in your Home folder). Also, [this page]("http://monkeyblog.org/ubuntu/installing/") will explain other ways to install software.

I think "all this terminal stuff" is a bit harsh. It's two commands that you can copy and amend from this page.

Gotta go (late for work) - good luck!

---

### Post by Partyboi2 on 2007-11-14
I just tried to install kiba-dock from this:
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)
And it worked ok for me, just alot of copying and pasting for newbie's :lolflag:

---

### Post by gutsynoob1 on 2007-11-14
ahhh, i did everything on that link and it still doesnt work, i give up

---

