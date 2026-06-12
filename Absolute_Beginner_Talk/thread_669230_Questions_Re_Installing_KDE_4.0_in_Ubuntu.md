---
title: "Questions Re: Installing KDE 4.0 in Ubuntu"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2008-01-16
Hi everyone,

I was hoping to give KDE a try without seriously messing up my Gnome-based Ubuntu installation. I know that one can install KDE from within Ubuntu via synaptic or aptitude, but I've got a few questions before I attempt to do so:

(1) I suspect that I will want to get rid of KDE at some point, if I remove it from within Synaptic will it remove all of its hundreds of dependencies as well? I don't want to do this if it's going to junk up my system too much.

(2) I've heard that installing KDE (not Kubuntu, just KDE) from within Ubuntu leads to the KDE and Gnome icons both being displayed in menus. Is there any way to have one desktop environment or the other running at any given time, rather than having this mishmash of Gnome and KDE?

(3) KDE 4.0, released just a week ago, looks pretty nice (as far as KDE goes anyway). I am assuming that version 4.0 isn't in the repositories yet. Is there a way to get that version of it installed without compiling from source myself (I'm not that advanced yet =)?

Thanks in advance!

---

### Post by finer recliner on 2008-01-16
2) in each desktop environment, you will have to manually edit their respective menus (in gnome its preferences > main menu). and remove any applications you do not want to see. and technically, you can have only one environment running at a time. but say you're in gnome, you can still run KDE applications, it just may take a few seconds longer to launch, because it has to load a bunch of extra libraries from KDE that arent already loaded into memory. in general, KDE applications run better in KDE, and gnome applications run better in gnome, but there is usually no problem in running an application in a different desktop environment

3) easy -> [http://www.kubuntu.org/announcements/kde4-rc2.php](http://www.kubuntu.org/announcements/kde4-rc2.php)

---

### Post by thisismalhotra on 2008-01-16
Just an update on the link, 

[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

one in the post above points to pre release instructions which should not be used anymore. I think if you removed kde4-core using sudo apt-get it should remove all the dependencies. If you don't mind use aptitude as that is better for dependency handling....

:)

---

### Post by plinydogg on 2008-01-18
Thanks to both of you!

---

### Post by plinydogg on 2008-01-21
I've encountered a roadblock. After running aptitude to install KDE, I am asked to uninstall Wicd, but I can't because it's the only way I access the Internet. Any way around this?

---

### Post by plinydogg on 2008-01-30
In other words, is there a way to leave WICD install and just decline to install whatever the KDE equivalent of Network Manager is?

---

### Post by plinydogg on 2008-01-30
<bump>

---

