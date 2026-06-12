---
title: "[SOLVED] Can I have gedit on Xubuntu?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by incen on 2008-02-15
Hi, everyone,

I plan to install gedit on my laptop Xubuntu. However, if I do "aptitude search gedit", I get nothing. Then, I do "sudo aptitude install gedit". It gives me

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "gedit"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 
```     

However, no package is found and I still cannot use gedit. Someone said he could install gedit. But why can't I? Could anyone help me with this? Or suggest me an edit as good as gedit? Thanks a lot!

---

### Post by aysiu on 2008-02-15
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by jordanmthomas on 2008-02-15
You should be able to install it no problem.
Did you maybe not have an internet connection when you first installed Ubuntu?
What's in your /etc/apt/sources.list ?

Also, you might want to try
```
sudo apt-get update
```
before installing gedit.

edit
beaten :|

---

### Post by Bruce M. on 2008-02-15
If I can install "X" programs in Gnome ( I use Thunar ) I see no reason why you can't.

Try the Synaptic Package Manager to install gedit, it will also grab all dependencies.

Bruce

---

### Post by spiderbatdad on 2008-02-15
you would need a lot of gnome libraries. You can create or copy someone's .nanorc to your home directory. Or choose from other text editors that work great in xfce: Medit, Scite, Geany.

heres a link to a discussion.[http://ubuntuforums.org/archive/index.php/t-368637.html](http://ubuntuforums.org/archive/index.php/t-368637.html)

---

### Post by incen on 2008-02-15
Well... still not...
Here are some results:

I did "sudo apt-get update" and it gave me:
```
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
```

Then, I did "sudo aptitude install gedit" and it gave me:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "gedit"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 
```

Here is cat /etc/apt/sources.list:
```
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by jordanmthomas on 2008-02-15
You need to disable the cd-rom as a source (put # in front of them) and enable the ones whose line start with "deb http...." by removing the #

Does xfce come with gksudo?
```
gksudo mousepad /etc/apt/sources.list
```

---

### Post by aysiu on 2008-02-15
The only source you have enabled right now is your Xubuntu CD.

[Get a fresh repositories list](http://www.psychocats.net/ubuntu/sources#key) and then try again.

---

### Post by jordanmthomas on 2008-02-15
It should look like this when you're done

> **incen said:**
> ```
#deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by spiderbatdad on 2008-02-15
most of your gusty download sites are commented out...see this thread to enable them.
[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

### Post by incen on 2008-02-15
Sweet! Now I'm installing gedit! I bet it will work! I don't know why the http one is commentted out. It doesn't make any sense. :confused:

---

### Post by incen on 2008-02-15
Well, now I have gedit but it's not colored version! I need one that can show different color when I write codes. How to fix it?

---

### Post by jordanmthomas on 2008-02-15
It was commented out because when you installed xubuntu, it couldn't verify that the repos were working.  So, rather than leave you with no chances of installing software, it used the CD as a repository to let you install at least SOME software.

You'll probably have a lot of updates now, too.  After you finish installing gedit, you may want to run
```
sudo apt-get upgrade
```

---

### Post by jordanmthomas on 2008-02-15
> **incen said:**
> Well, now I have gedit but it's not colored version! I need one that can show different color when I write codes. How to fix it?
To get syntax highlighting, just save your file.  It usually detects the filetype and turns on syntax highlighting. If it doesn't, try view --> highlight mode and choose the appropriate one.

---

### Post by aysiu on 2008-02-15
> **incen said:**
> Well, now I have gedit but it's not colored version! I need one that can show different color when I write codes. How to fix it?
Go to View > Highlight Mode and select what language you're using.

---

### Post by spiderbatdad on 2008-02-15
have you tried naming the document with the appropriate tag...like .sh?

---

### Post by incen on 2008-02-15
Yeah, I named it .c. It seems the problem is I have to hit Enter to make it change color. :P
But, anyway, I'm happy to learn another trick on gedit! Thank you all, guys! :KS

---

### Post by spiderbatdad on 2008-02-15
Hmmm. I dont have to hit enter in C but do have to complete a "good" line.
This may be due to the need for the line to be interpreted by the c libs.

Have you installed the package build-essential  and build-essential builtins? That might help.

---

### Post by spiderbatdad on 2008-02-15
In other words: If I type: #include <stdio.h   there is no color. But when I compete the command:
#include <stdio.h>  the line gets interpreted and colorizes.

---

