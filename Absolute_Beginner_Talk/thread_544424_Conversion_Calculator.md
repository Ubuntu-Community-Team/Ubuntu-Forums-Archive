---
title: "Conversion Calculator"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-06
I'm looking for a conversion calculator that will tell me
different conversions.

Example: 196.080 Kilobytes = Megabytes ?

---

### Post by 505 on 2007-09-06
Try 'convertall' it is in the repos.

---

### Post by Orbital75 on 2007-09-06
thank you....  :KS

---

### Post by Orbital75 on 2007-09-06
Well, I installed it and it put it in /usr/bin/convertall
I believe the file to open is convertall.pyc
For some reason it won't open.

I was hoping it would put an icon in the Accessories menu but
it didn't.

How do I get it to work. I don't see any instructions
and form what is see all the Dependencies were installed.

---

### Post by hyper_ch on 2007-09-06
Why didn't you install it from the repos?

---

### Post by Orbital75 on 2007-09-06
I did..... I guess you haven't install it before.  :)
Any idea how to run it?

---

### Post by Paulmd on 2007-09-06
> **Orbital75 said:**
> I did..... I guess you haven't install it before.  :)
Any idea how to run it?

Works here
```
paul@paul-desktop:~$ sudo apt-get install convertall
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfame-0.9 libpvm3 libxalan110 libpostproccvs51 libx264-54 transcode
  libavutilcvs49 libavcodeccvs51 libxerces27 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python-qt4 python-sip4
Suggested packages:
  python-qt4-dbg python-sip4-dbg
Recommended packages:
  python-elementtree
The following NEW packages will be installed:
  convertall python-qt4 python-sip4
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 3722kB of archives.
After unpacking 17.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com feisty/main python-sip4 4.5-0ubuntu2 [132kB]
Get:2 http://us.archive.ubuntu.com feisty/main python-qt4 4.1-0ubuntu6 [3535kB]
Get:3 http://us.archive.ubuntu.com feisty/universe convertall 0.4.0-0ubuntu1 [54.1kB]
Fetched 3722kB in 6m33s (9451B/s)                                              
Selecting previously deselected package python-sip4.
(Reading database ... 125461 files and directories currently installed.)
Unpacking python-sip4 (from .../python-sip4_4.5-0ubuntu2_i386.deb) ...
Selecting previously deselected package python-qt4.
Unpacking python-qt4 (from .../python-qt4_4.1-0ubuntu6_i386.deb) ...
Selecting previously deselected package convertall.
Unpacking convertall (from .../convertall_0.4.0-0ubuntu1_all.deb) ...
Setting up python-sip4 (4.5-0ubuntu2) ...

Setting up python-qt4 (4.1-0ubuntu6) ...

Setting up convertall (0.4.0-0ubuntu1) ...
paul@paul-desktop:~$ convertall
487 units loaded

```

---

### Post by ubuntu27 on 2007-09-07
> **505 said:**
> Try 'convertall' it is in the repos.

WoW! Pretty good application, didn't know of it before. Thank you.

> **Orbital75 said:**
> I'm looking for a conversion calculator that will tell me
different conversions.

Example: 196.080 Kilobytes = Megabytes ?


I also recommend a app called Qalculate!   
Qalculate! Let's you do different mathematical calculation (velocity, speed, temperature, volumen, area, etc), it let's you add variables, and there is also monetary (Currency) conversion, and more.

It has two different version one for gtk (GNOME, XFCE) and KDE.

Ubuntu (GNOME) or Xubuntu (XFCE):

```
sudo aptitude install qalculate-gtk
```

Kubuntu (KDE):

```
sudo aptitude install qalculate-kde
```

---

### Post by ubuntu27 on 2007-09-07
> **Orbital75 said:**
> I did..... I guess you haven't install it before.  :)
Any idea how to run it?

I know what you mean, when you installed it didn't appeard in the menus.

type ```
convertall
``` in the terminal and press enter. Did anything happen?

---

### Post by dwhitney67 on 2007-09-07
> **Orbital75 said:**
> Well, I installed it and it put it in /usr/bin/convertall
I believe the file to open is convertall.pyc
For some reason it won't open.

I was hoping it would put an icon in the Accessories menu but
it didn't.

How do I get it to work. I don't see any instructions
and form what is see all the Dependencies were installed.

The 'converter' application should be in /usr/bin.

If you want to add it to your Applications menu (perhaps under Accessories), then run this command from a terminal to set it up:

[FONT="Courier New"]$ alacarte[/FONT]

Why in pray-tell 'alacarte' is not in the Applications -> Accessories menu and why 'converter' didn't get added too is a "mystery"... probably just an oversight by the Ubuntu coders.

---

### Post by overdrank on 2007-09-07
> **505 said:**
> Try 'convertall' it is in the repos.

Thanks cool stuff !!!!  :guitar:

---

### Post by skyjacker on 2007-09-07
> **dwhitney67 said:**
> The 'converter' application should be in /usr/bin.

If you want to add it to your Applications menu (perhaps under Accessories), then run this command from a terminal to set it up:

[FONT="Courier New"]$ alacarte[/FONT]

Why in pray-tell 'alacarte' is not in the Applications -> Accessories menu and why 'converter' didn't get added too is a "mystery"... probably just an oversight by the Ubuntu coders.
Great help, I also installed this last week, and could not find it in the Applications section. I was going to remove it but glad I didn't cause now it works. Thanks:):):)

---

### Post by Campingman on 2007-09-07
Thanks 505

Had not heard of this one, looks good.  One to add to my must install list.
Same issue with not adding to the menu.  Added it with the menu editor

---

### Post by ubuntu27 on 2007-09-07
By the way the Manu Editor "Alcate" can be access by

Right clicking the menus (Application, Places, or System) and selecting "Edit Menus"

---

