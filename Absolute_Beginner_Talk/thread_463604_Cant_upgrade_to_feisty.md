---
title: "Cant upgrade to feisty"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Fsngruv on 2007-06-03
I am attempting to upgrade from Dapper to Fiesty, but I'm having a problem when I run the update manager, everytime i attemp to apt-get anything I run into this problem where is says that dpkg-dev is unable to update, so i go to synaptic package manager and it tells me that 

The following packages have unresolvable dependencies. make sure that all required repositories are added and enabled in preferences
          dpkg-dev:
  Depends: dpkg (>=1.13.20) but 1.13.11ubuntu7 is to be installed

it shows my current version as 1.13.11ubuntu7 and the latest version as 1.13.24ubuntu6

I'm a relative noob, and this is a little over my head

---

### Post by oilchangeguy on 2007-06-03
you can't go from 6.06 straight to 7.04. you'll need to install 6.10 first. or back up your data and do a fresh install of 7.04.

---

### Post by loathsome on 2007-06-03
I highly recommend a fresh install.

---

### Post by Fsngruv on 2007-06-03
I realize that i need to upgrade to edgy first but i'm trying to avoid the fresh install because of all the time i've invested in customizing, any help with my problem

---

### Post by oilchangeguy on 2007-06-03
> **Fsngruv said:**
> I realize that i need to upgrade to edgy first but i'm trying to avoid the fresh install because of all the time i've invested in customizing, any help with my problem

you could have made it known you already knew about having to go thru 6.10 first. read this:
[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)
nothing like having the remnents of three operating systems on your computer to possibly screw things up. it's always best to do a fresh install.

---

### Post by zvacet on 2007-06-04
> I realize that i need to upgrade to edgy first but i'm trying to avoid the fresh install because of all the time i've invested in customizing, any help with my problem

Make sure that your Dapper is up-to-date and after that type in terminal

```
gksu "update-manager -c"
```

When upgrade is completed change your source list fro Dapper to Edgy

```
  sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

To upgrade to Feisty

[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")

and after that change sourcce list 

```
 sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

**Before you start doing anything comment (put # sign in front of line)every unofficial repos.**

---

### Post by Fsngruv on 2007-06-04
that did it, thanks allowed me to upgrade and fixed my dpkg-dev problem, appreciate it

---

