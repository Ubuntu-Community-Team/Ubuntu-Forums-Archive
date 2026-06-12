---
title: "Missing Packages"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by MugenDraco on 2007-04-24
Even though I've been using Linux for a while, I'm still a newbie.  Needless to say, I use Ubuntu.  I love the easy-to-use package manager, but I upgraded to 7.04, it kept freezing on me, so I downgraded back to 6.06.  My problem is that before I used MPlayer for all my videos because it was the only player that would play everything no questions asked.  I also used Graveman for burning DVDs cuz it was simple to use.  But both of these programs seem to have been removed from the package manager, and Totem won't play any videos.

---

### Post by nsleiman on 2007-04-24
why dont you just download those missing packages ? any difficulties ?

---

### Post by Najand on 2007-04-24
I think you received the message saying: "All third party repositories has been disabled" when trying to upgrade your computer to 7.04. Well, to solve your problem, open a terminal and edit /etc/apt/sources.list:
```

gksu gedit /etc/apt/sources.list

```
Then remove all "#" marks from the lines starting with "deb" or "deb-src" words.
After finishing it, save it. and run the following in the temrinal:
```

sudo apt-get update

```

---

### Post by oilchangeguy on 2007-04-24
install and use automatix. [www.getautomatix.com](www.getautomatix.com). you'll be able to find the needed codecs, and much more.

---

### Post by Najand on 2007-04-24
> **oilchangeguy said:**
> install and use automatix. [www.getautomatix.com](www.getautomatix.com). you'll be able to find the needed codecs, and much more.

Well, if you have lots of space on your harddisk you want to waste, using automatix is fine, but I personally think using such softwares, prevent people to learn configurations they must learn themselves.

---

### Post by oilchangeguy on 2007-04-24
what is it that has led you to belive automatix takes up a lot of space? it simply automates the install process of certain programs. it does not store them all on your hard drive. i'm running version 6.06 on a 30gb hd, with 27gb of free space. and i've got automatix installed on this computer. also where is it written that every linux user must be a command line junkie?

---

### Post by zvacet on 2007-04-24
Did you look in add/remove programs?
[http://gnomefiles.org/app.php/MPlayer]("http://gnomefiles.org/app.php/MPlayer")

---

### Post by Najand on 2007-04-24
> **oilchangeguy said:**
> what is it that has led you to belive automatix takes up a lot of space? it simply automates the install process of certain programs. it does not store them all on your hard drive. i'm running version 6.06 on a 30gb hd, with 27gb of free space. and i've got automatix installed on this computer. also where is it written that every linux user must be a command line junkie?

I don't want to go to that topic again, maybe the following link help you to know what I mean:
[http://ubuntuforums.org/showthread.php?t=257131]("http://ubuntuforums.org/showthread.php?t=257131")

---

### Post by oilchangeguy on 2007-04-24
show me proof that automatix uses lots of hard drive space. like i said, my computer has used a little over 3gb. a clean install of xp pro sp2 and all of the available microsoft updates takes almost 5gb of space, and that's just the os.

---

### Post by Najand on 2007-04-24
I have installed this computer with Breezy and have been upgrading it todapper/edgy/feisty and I am just using 1.5GB (all partitions except /home),. Maybe you have some applications I don't have. But 3 GB for an OS is pretty big. Give me a reason why he/she should install automatix when he/she  needs "mplayer"?

---

### Post by oilchangeguy on 2007-04-24
you've still not shown me proof. and so what if it does. most modern computer users have a computer with a hard drive larger than 10gb. i don't see your point.

---

### Post by MugenDraco on 2007-04-24
thanx to Najand i now have a lot more packages in the package manager, and i know have Xine and Graveman, but still no MPlayer.  Xine is about like Totem too.  It won't play anything.  i already tried installing MPlayer manually, but it keeps giving me an error when i run ./configure.  it says something about upgrading to gcc 3.0 or 4.0.  i did, but it still gives me the error.  i also tried the add/remove programs thing, but MPlayer wasn't listed there either.  i wanna try automatix, but the packages only come in .deb format, and i don't know how to install those kinds of packages.  i'm only familiar with tarballs.

---

