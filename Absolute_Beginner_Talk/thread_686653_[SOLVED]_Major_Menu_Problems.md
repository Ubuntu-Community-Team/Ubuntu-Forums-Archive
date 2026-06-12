---
title: "[SOLVED] Major Menu Problems"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Riverbanks on 2008-02-03
Ok, I'm having HUGE problems with the Applications/Places/System menu.  Several things in it will not open at all.  Just to give you an idea, I can't open:

Applications > Add/Remove
System > Preferences > Advanced Desktop Effects Settings
System > Preferences > Default Printer
System > Preferences > Hardware Information
System > Preferences > Main Menu
System > Administration > Language Support
System > Administration > Printing
System > Administration > Restricted Drivers Manager
System > Administration > Screens and Graphics
System > Administration > Software Sources
System > Administration > Update Manager

When I click on any of these, nothing happens at all.  This problem just started today, and this is a fresh install of Ubuntu, so I have no idea what could have caused it.  I didn't do any drastic changes to the system, or really anything that could have caused it.

Any ideas?

---

### Post by philinux on 2008-02-03
When you installed were you connected to the internet?

Go to the terminal and use

cat /etc/apt/sources.list

post the result.

---

### Post by Riverbanks on 2008-02-03
Yes, I was connected to the internet when I installed.  

Here's my results from cat /etc/sources.list:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# AWN
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

---

### Post by philinux on 2008-02-03
That looks fine. 

Maybe its the ubuntu desktop thats got messed up somehow. Odd for a fresh install were there any error messages?

I assume you tried rebooting.

---

### Post by Riverbanks on 2008-02-03
Nope, no error messages, and I've rebooted several times.

Its strange, I just used Add/Remove earlier today and it worked just fine, now it and several other things just broke out of the blue...

---

### Post by philinux on 2008-02-03
One of the items, main menu is called alacarte.

In terminal type the command

alacarte

note any errors.

---

### Post by Riverbanks on 2008-02-03
Alright, heres what I got:

/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: PyUnicodeUCS2_AsUTF8String

I guess that import error might have something to do with it?

---

### Post by philinux on 2008-02-03
I notice you've got AWN installed, from another thread. Is there a coincidence here?

---

### Post by Riverbanks on 2008-02-03
I don't think AWN has anything to do with it, I started noticing this problem before I installed it, (when I tried to use Software Sources) but I didn't see how bad it was until after.

---

### Post by philinux on 2008-02-03
Seen before too.

Googled this  File "/usr/bin/alacarte", line 22, in <module and 
got this [http://ubuntuforums.org/showthread.php?p=4245117](http://ubuntuforums.org/showthread.php?p=4245117)

I'd google for some of the error lines you got

---

### Post by jan quark on 2008-02-03
just a guess

run 

```
sudo apt-get -f install
```

to fix all would-be broken packages

---

### Post by nikef on 2008-02-03
Hi
i am also getting this problem 2,but mine is not a fresh install

i can use the internet,but can not use applications,places ,system 

i can not switch my pc off ,just had 2 hard reboot,this all started a couple days ago when i switched on compiz :confused: ,why oh why did i switch that on.how can i turn off or uninstall :mad:

---

### Post by Riverbanks on 2008-02-03
Hey, I fixed it!

I went into Synaptic and reinstalled python-cairo, and that fixed the whole problem.

Thanks man. :)

---

