---
title: "wine"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-07
does anyone know what has happened here???
iv put the repositories in perfect.
i tryed adding them with synaptic and i have also tryed adding them manually with nautilus and editing the etc/apt/sources.list

this is what happens when i type the sudo aptitude install wine  command in the terminal

```
   ***sphinx*** sudo aptitude install wine
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for wine
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
   
```


[edit] iv tryed the apt-get install wine aswell.this is what i get...


```
  ***sphinx*** sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
 ***sphinx*** come to me wine.il take good care of you.
bash: come: command not found
 ***sphinx*** well **** you then you alcoholic dickhead
bash: well: command not found
 ***sphinx***
 
```

---

### Post by CatKiller on 2006-10-07
> **uk_sphinx said:**
> [edit] just been back to there site, what is apt-get install wine ????
what does this do differently from aptitude install???
it dosnt say on there site

[aptitude versus apt-get]("http://www.psychocats.net/ubuntu/aptitude")

---

### Post by Delkster on 2006-10-07
> **uk_sphinx said:**
> does anyone know what has happened here???
iv put the repositories in perfect.
i tryed adding them with synaptic and i have also tryed adding them manually with nautilus and editing the etc/apt/sources.list

this is what happens when i type the sudo aptitude install wine  command in the terminal

Have you tried to see if you can find the wine package in Synaptic? If not, I'd still guess that there's something wrong with your repository settings or something. You may also need to refresh your local package database from the repositories if you haven't done that after configuring the repositories:
```
sudo apt-get update
```

---

### Post by Sef on 2006-10-07
Have you enabled the [Universe and Multiverse repositories?]("https://help.ubuntu.com/community/Repositories/Ubuntu#what")

---

### Post by BLTicklemonster on 2006-10-07
My sig has a nice link on how to get wine installed with winetools and everything else.

---

### Post by uk_sphinx on 2006-10-07
you know,
i set all the extra repositorys up ages ago.
the strangest thing is happening now.
when i click on the various catagorys, add, there not highlighted.
so, i highlight them, click add, click close, reload, then go back to them and there not highlighted again.
iv tried them all but they wont stay highlighted.
god damn it im getting fed up with ubuntu.

i was programming last night on my own project. bloody ubuntu closed the application without me saving and i lost 2 hours work.
you'l never understand what thats like for a newbie programmer who puts his heart into it.
i cant take it much longer.

[edit]  >   My sig has a nice link on how to get wine installed with winetools and everything else. 

yeah its not bad, the first link is broke so you may aswell get rid of that.

---

### Post by uk_sphinx on 2006-10-07
think iv got it now.
their repository isnt working for me for some reason.
but i have manged to download the source code for it.
im going to have to compile it myself.

everythings a chore.
i bet il be dissapointed with it anyway

---

### Post by BLTicklemonster on 2006-10-07
> **uk_sphinx said:**
> 

yeah its not bad, the first link is broke so you may aswell get rid of that.

This gimp tutorials link? I just went there and it worked fine.

---

### Post by lanchongzi on 2006-10-08
Hi there
I cant get my chinese Adsl modem ZXDSL 831ii to start wich leads me to the problem of not being able to download wine :(
are there other ways of getting it?
i tried downloading it on a different PC then adding it to mine but some thing about a universe kept me from doing it.
wht can i do ?

---

### Post by Delkster on 2006-10-10
> **uk_sphinx said:**
> think iv got it now.
their repository isnt working for me for some reason.
but i have manged to download the source code for it.
im going to have to compile it myself.
You could also find the prebuilt package on their [Debian/Ubuntu package archive page](http://wine.budgetdedicated.com/archive/index.html), download it and install it by hand. That may not be as nice as having the repository enabled (for example, you don't get automatic updates) but it probably beats compiling it from source -- after all, installing it on Ubuntu should be just double-clicking on the package.

> everythings a chore.
i bet il be dissapointed with it anyway
You surely will if you want to be.


lanchongzi, you might also be able to try downloading the package directly from the archive page and then installing it on the other computer but you might run into missing dependencies. They're automatically satisfied when installing but only if the necessary packages are accessible, and they aren't if they're only available in online repositories and you don't have a 'net connection.

---

### Post by BLTicklemonster on 2006-10-10
As far as the link in my sig, I am sure that if you use a newer version of wine, then use winetools, the only problem you will have could be internet explorer. If so, then this link will give you a working Internet Explorer [http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u](http://www.ubuntuforums.org/showthread.php?t=267469&highlight=internet+explorer+4+u)

So don't be afraid to try the link in my sig, just apt-get install wine, then pick up at winetools, and follow the instructions from there. If IE doesn't work, then install the one I link up there.

---

