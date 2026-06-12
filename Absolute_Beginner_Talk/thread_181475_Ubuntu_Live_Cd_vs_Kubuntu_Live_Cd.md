---
title: "Ubuntu Live Cd vs Kubuntu Live Cd"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2006-05-24
Is it better to get a ubuntu live cd or a kubuntu live cd

---

### Post by Sef on 2006-05-24
The biggest advantage to getting Ubuntu is that most people in here use it, so more help available.  

From the CD standpoint, they are both good.  Your preference is all that matters.

---

### Post by ProjectGod on 2006-05-24
kubuntu implements KDE?

i heard KDE was a little more resource intensive than GNOME. so if you have an older machine with limited processing powers go for ubuntu. :mrgreen:

---

### Post by Lord Illidan on 2006-05-24
[quote=ProjectGod]kubuntu implements KDE?

i heard KDE was a little more resource intensive than GNOME. so if you have an older machine with limited processing powers go for ubuntu. :mrgreen:[/quote]

Actually, they are quite the same in processing resources in my exp.

Xubuntu is the best for limited processing powers, but I don't know about a live cd for that one.

If you are really limited, try Damn Small Linux....rocks!

---

### Post by youthforlinux on 2006-05-24
well my linuxbox is pretty good and runs pretty quick

*but i was wondering whether it is better to install kubuntu first then install gnome or vice versa

---

### Post by Lord Illidan on 2006-05-24
[quote=youthforlinux]well my linuxbox is pretty good and runs pretty quick

*but i was wondering whether it is better to install kubuntu first then install gnome or vice versa[/quote]

Can do.

You can install kubuntu/ubuntu/xubuntu from any three of them, in fact.
Just do

sudo apt-get install kubuntu-desktop

sudo apt-get install ubuntu-desktop

sudo apt-get install xubuntu-desktop

But do you intend to use a LIVE CD for all this?

---

### Post by aysiu on 2006-05-24
[QUOTE=Lord Illidan]Can do.

You can install kubuntu/ubuntu/xubuntu from any three of them, in fact.
Just do

sudo apt-get install kubuntu-desktop

sudo apt-get install ubuntu-desktop

sudo apt-get install xubuntu-desktop

But do you intend to use a LIVE CD for all this?[/QUOTE] Better yet, install them with aptitude instead of apt-get. Makes it easier to remove them later should you wish to do so.

---

### Post by youthforlinux on 2006-05-24
[QUOTE=Lord Illidan]Can do.

You can install kubuntu/ubuntu/xubuntu from any three of them, in fact.
Just do

sudo apt-get install kubuntu-desktop

sudo apt-get install ubuntu-desktop

sudo apt-get install xubuntu-desktop

But do you intend to use a LIVE CD for all this?[/QUOTE]

Cuz i wanted to try out the live CD installer for Dapper

---

### Post by youthforlinux on 2006-05-24
[QUOTE=aysiu]Better yet, install them with aptitude instead of apt-get. Makes it easier to remove them later should you wish to do so.[/QUOTE]

Why can't *apt-get* get rid of them
though i don't really intend and just wondering why i would get rid of them though?

---

### Post by Lord Illidan on 2006-05-24
[quote=youthforlinux]well my linuxbox is pretty good and runs pretty quick

*but i was wondering whether it is better to install kubuntu first then install gnome or vice versa[/quote] 

I've never used aptitude.

Aysiu, can't one type apt-get remove --purge ubuntu-desktop for example?

---

### Post by youthforlinux on 2006-05-24
[QUOTE=Lord Illidan]Can do.

You can install kubuntu/ubuntu/xubuntu from any three of them, in fact.
Just do

sudo apt-get install kubuntu-desktop

sudo apt-get install ubuntu-desktop

sudo apt-get install xubuntu-desktop

But do you intend to use a LIVE CD for all this?[/QUOTE]
 Cuz i want to use the live CD installer for Dapper

---

### Post by aysiu on 2006-05-24
[QUOTE=youthforlinux]Cuz i want to use the live CD installer for Dapper[/QUOTE] So you would use the live CD, install Dapper, then add on other desktop environments?

If that's the case, these three links should help you out:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by youthforlinux on 2006-05-24
[QUOTE=aysiu]So you would use the live CD, install Dapper, then add on other desktop environments?

If that's the case, these three links should help you out:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)[/QUOTE]

sweet thans aysiu
are u the master of all things ubuntu?

---

### Post by xtacocorex on 2006-05-24
[QUOTE=Lord Illidan]I've never used aptitude.

Aysiu, can't one type apt-get remove --purge ubuntu-desktop for example?[/QUOTE]

Seeing as I'm not aysiu, but I know the answer, because of one of aysiu's threads, I'll explain.

apt-get doesn't keep track of the dependencies installed with a meta-package so if you remove ubuntu-desktop, you just remove that package. With aptitude, it knows what got installed with it and will also uninstall them all when the meta-package is removed.

If I remember correctly, the --purge is for removing configuration files from the package.

---

