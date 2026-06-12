---
title: "Picture management out of range"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by hannulan on 2007-07-11
I just did an upgrade from dapper to edgy (yes, I know I'm a bit late). But I have some problem, I think is something with the xserver. 

When I start my computer I get to the login window. I can write my username and password but after that the only thing I see is a message from the monitor which tells me "Picture management is out of range". After that I have to login in text mode.

I have tried to explicity state the HorizSync och VertRefresh parameters to what is stated in the specification for the monitor. I have also checked so the resolution is correct. But the xserver do show me something (in the beginning when I try to login) so maybe that is not the fault. 

I have Matrox Graphics MGA G400 AGP graphic card and the xorg.conf file tells me that it should use the mga driver (which I checked was installed). The monitor I use is an Ergovision 735 TCO99.

Does anyone have a clue where I should continue look for the fault?

---

### Post by hamburglar6 on 2007-07-12
You might want to just scrap your old xorg.conf file and generate a new one using:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

I remember when I upgraded to edgy nothing really worked right- it made life a lot easier to just backup important data and do a fresh install.

---

### Post by hannulan on 2007-07-12
I run this dkpg-reconfigure program yesterday when I was trying to install edgy, but it didn't make my life better. 

I talked to a friend this morning and he told me that there are a bug in the Xserver-version comming with edgy so it does not work correctly with the graphic card I use. So I will try to do a dist-upgrade to feisty and see if that makes life better.

---

### Post by hannulan on 2007-07-13
The idst-upgrade for feisty didn't help me. There are a lot of broken packages so the upgrade those not succeed.

I have tried "sudo aptitude (apt-get) -f dist-upgrade" to try to force aptitude (apt-get) to remove the broken packages. This doesn't make any changes. 

Are there some way to remove a bunch of packages easy or to remove all broken packages?

---

### Post by hamburglar6 on 2007-07-13
When feisty first came out they issued a million warnings about using update manager instead of dist-upgrade going from edgy --> feisty because of problems with broken packages.  If 

```
 sudo apt-get autoremove 
```
and
```
 sudo apt-get install -f 
```

did not work, and your /etc/apt/sources.list file is in order (if you don't know what is supposed to be in it here is a good link for automatically generating one you can just paste into the file: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) )  then I would strongly recommend backing up any files you need and doing a fresh install; in all likelihood it will be a much simpler process.

---

### Post by hannulan on 2007-07-16
I did a fresh install of Ubuntu. Now everything works. The backup was not so difficult so it was definitly worth it.

---

