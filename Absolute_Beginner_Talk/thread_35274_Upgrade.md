---
title: "Upgrade"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by ingrid on 2005-05-18
How to upgrade my ubuntu warty to hoary ?

---

### Post by dave9191 on 2005-05-18
Have a read through [the wiki](http://www.ubuntulinux.org/wiki/UpgradingFromWartyWarthogToHoaryHedgehog/view?searchterm=warty%20to%20hoary) 

Or do a fresh intstall, but that will cause you to loose any settings and files you have unless you back them up first. 


Dave

---

### Post by XDevHald on 2005-05-18
[QUOTE=ingrid]How to upgrade my ubuntu warty to hoary ?[/QUOTE]
 Easy Enough

type in a terminal window: [b]sudo gedit /etc/apt/sources.list

[/b]Replace it with the sources.list below

>                               deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted
 
 ## Uncomment the following two lines to fetch major bug fix updates produced
 ## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
 
 ## Uncomment the following two lines to add software from the 'universe'
 ## repository.
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 ## team, and may not be under a free licence. Please satisfy yourself as to
 ## your rights to use the software. Also, please note that software in
 ## universe WILL NOT receive any review or updates from the Ubuntu security
 ## team.
 deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe
 
 deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
 
 deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
 
 deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse
 deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse

---

### Post by ingrid on 2005-05-19
thanks for your help.
I have another problem. when I try to start the Synaptic package manager (graphical interface), a popup window appear with this error message :
 [COLOR=Red]Failed to run /usr/sbin/synaptic as user root:
 Child terminated with 1 status[/COLOR]

AND when I try to start in CLI, with this command : [COLOR=DarkGreen]/usr/sbin/synaptic[/COLOR]
I have this error message :
[COLOR=Red](synaptic:29752): Gtk-WARNING **: cannot open display:[/COLOR]

Must I re-install the Synaptic manager ?

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=ingrid]thanks for your help.
I have another problem. when I try to start the Synaptic package manager (graphical interface), a popup window appear with this error message :
 [COLOR=Red]Failed to run /usr/sbin/synaptic as user root:
 Child terminated with 1 status[/COLOR]

AND when I try to start in CLI, with this command : [COLOR=DarkGreen]/usr/sbin/synaptic[/COLOR]
I have this error message :
[COLOR=Red](synaptic:29752): Gtk-WARNING **: cannot open display:[/COLOR]

Must I re-install the Synaptic manager ?[/QUOTE]


You don't need synaptic. Open up the regular terminal. Do what BB said. then type:

sudo apt-get update

the when that is done:

sudo apt-get dist-upgrade

that will upgrade you just as synaptic would (synaptic is a pretty cover for apt-get)

For the record, that error you get with synaptic means you gave it the wrong password.

---

### Post by ingrid on 2005-05-20
[QUOTE=poofyhairguy]You don't need synaptic. Open up the regular terminal. Do what BB said. then type:

sudo apt-get update

the when that is done:

sudo apt-get dist-upgrade

that will upgrade you just as synaptic would (synaptic is a pretty cover for apt-get)

For the record, that error you get with synaptic means you gave it the wrong password.[/QUOTE]
 Thanks
You resolved my problem.
;-)

---

### Post by agger on 2005-05-20
[QUOTE=ingrid]How to upgrade my ubuntu warty to hoary ?[/QUOTE]
 In the other "upgrade" thread started by myself, I was given this advice as to updating:

> 
In theory each verison is upgradable and this is stated by canonical (ie Warty to Hoary, Hoary to Breezy). I went from Warty to Hoary and found no probs with 3rd party drives or software packages. You shouldn't need to do more than 

sudo apt-get update
sudo apt-get dist upgrade


As I won't be doing this before Breezy is stable, I haven't tried it - but at least it is known to have worked!

---

### Post by kumakun on 2005-05-20
Out of curiousity and not to jenk the thread, but what's the process if I were to do a fresh install of Warty, and then upgrade from the Hoary CD?  Is it the same apt-get process without the changes to the repositories? Or is there something special I need to do further?

/Kuma

---

