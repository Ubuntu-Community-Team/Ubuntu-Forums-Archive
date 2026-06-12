---
title: "Software Sources, Synapic Repositiories, GDebi Broken"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by cwk on 2007-05-08
Software Sources: Looks like it opens for a split second, then closes.

Synaptic: Can't open repositories list.

GDebi Package Manager: Doesn't do anything.

This was a clean install. What's going on here, and how do I fix it?

---

### Post by jfinkels on 2007-05-09
> **cwk said:**
> Software Sources: Looks like it opens for a split second, then closes.

Synaptic: Can't open repositories list.

GDebi Package Manager: Doesn't do anything.

This was a clean install. What's going on here, and how do I fix it?

Use the command line? :P

Really, I don't know. Perhaps there's something wrong with your /etc/apt/sources.list. Can you post the output of ```
cat /etc/apt/sources.list
``` so that we can see if anything is wrong with it?

---

### Post by cwk on 2007-05-09
> **jfinkels said:**
> Use the command line? :P

Really, I don't know. Perhaps there's something wrong with your /etc/apt/sources.list. Can you post the output of ```
cat /etc/apt/sources.list
``` so that we can see if anything is wrong with it?

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by jfinkels on 2007-05-09
Everything looks okay there...are you using these applications as the superuser? Here's more info on that: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Do you get any error messages when you try to open synaptic from the terminal? Type the following:
```

gksudo synaptic

```

---

### Post by cwk on 2007-05-11
> **jfinkels said:**
> Everything looks okay there...are you using these applications as the superuser? Here's more info on that: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Do you get any error messages when you try to open synaptic from the terminal? Type the following:
```

gksudo synaptic

```

Hmm . . . no messages when I open synaptic from the terminal, but I do get this when I try to open the repositories:

```
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 25, in <module>
    import apt
  File "/usr/lib/python2.5/site-packages/apt/__init__.py", line 7, in <module>
    from apt.package import Package
ImportError: cannot import name Package
```

---

### Post by jfinkels on 2007-05-11
> **cwk said:**
> Hmm . . . no messages when I open synaptic from the terminal, but I do get this when I try to open the repositories:

```
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 25, in <module>
    import apt
  File "/usr/lib/python2.5/site-packages/apt/__init__.py", line 7, in <module>
    from apt.package import Package
ImportError: cannot import name Package
```

That's very unusual, I'm afraid I don't know how to help you from here. But at least we know where the problem is...for some reason, python can't import the Package class from the apt.package module.

---

### Post by cwk on 2007-05-13
Hmm . . . anyone have any ideas here?

---

### Post by zvacet on 2007-05-13
I don´t know will it help but try it anyway
```
sudo aptitude update
```

And maybe before try that this lines # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
look like deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

---

### Post by cwk on 2007-05-20
> **zvacet said:**
> I don´t know will it help but try it anyway
```
sudo aptitude update
```

And maybe before try that this lines # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
look like deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

Yeah, tried all that. Still nothing.

Also, Add/Remove programs doesn't work. It shows that it's starting up, and then nothing happens. 

This is really starting to get frustrating. I don't want to do another install, but it's starting to look like I might have to. 

Is there another good package installer other than GDebi? Is there another add/remove GUI out there?

Anybody have any other ideas?

---

### Post by cwk on 2007-05-23
Last plea for help here.

---

