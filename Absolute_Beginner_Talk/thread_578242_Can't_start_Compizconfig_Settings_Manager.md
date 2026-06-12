---
title: "Can't start Compizconfig Settings Manager"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by hotweiss on 2007-10-17
Here's the error I get when I try to run ccsm in terminal:

> Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'


I installed Compiz Fusion exactly the same way as per the wiki insturctions...

Here's what  dpkg -l | grep compiz gives me:

> 
ii  compiz                                     0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager
ii  compiz-core                                0.3.6-1ubuntu13                        OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070917-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070917-0ubuntu3~ppa1        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.3.6-1ubuntu13                        OpenGL window and compositing manager - GNOM
ii  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.3.6-1ubuntu13                        OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2~ppa1        Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings

plu
Now here's another problem, I can't even upgrade compiz-core, compiz-gnome and compiz-plugins using the update manager because I get some error telling me that not all updates can be installed... so it offers me a partial upgrade, when I click on partial upgrade I get an error saying that the packages cannot be authenticated.

---

### Post by hotweiss on 2007-10-17
bump

---

### Post by bromix on 2007-10-17
What graphics card are you using?

---

### Post by Seisen on 2007-10-17
What wiki are you talking about too?

---

### Post by Drakkor on 2007-10-17
Why don't you upgrade to Gutsy? , that may help........ :)

---

### Post by ThrobbingBrain66 on 2007-10-17
It looks to me like you have more than one repository supplying compiz packages to you.  This would explain the updating problems and conflicting packages (having .3.6 and .5.2 packages installed at the same time).

Can you post the output of the following command please?

```
cat /etc/apt/sources.list
```

---

### Post by bromix on 2007-10-17
> **ThrobbingBrain66 said:**
> It looks to me like you have more than one repository supplying compiz packages to you.  This would explain the updating problems and conflicting packages (having .3.6 and .5.2 packages installed at the same time).

Can you post the output of the following command please?

```
cat /etc/apt/sources.list
```

Just my edcuational sake..:)  Can you tell me how you knew that from the outputs the OP posted?  Not sarcastic in ANY way, i just would like to know.

---

### Post by ThrobbingBrain66 on 2007-10-17
> **bromix said:**
> Just my edcuational sake..:)  Can you tell me how you knew that from the outputs the OP posted?  Not sarcastic in ANY way, i just would like to know.

Certainly. :)

Look in the first post where the OP quotes the Compiz packages he has installed.  Some are from version .3.6 and some are from .5.2.  This should not be (all packages should be the same version).  

You'll also see that the .5.2 packages have '~ppa1' as part of the package name, while the .3.6 packages don't.  All packages from a single repo should have a common naming convention.  This is another indicator that they are from different repositories.

Naturally, the mixing of two different versions/repos of the same package can lead to breakage.

---

### Post by bromix on 2007-10-17
> **ThrobbingBrain66 said:**
> Certainly. :)

Look in the first post where the OP quotes the Compiz packages he has installed.  Some are from version .3.6 and some are from .5.2.  This should not be (all packages should be the same version).  

You'll also see that the .5.2 packages have '~ppa1' as part of the package name, while the .3.6 packages don't.  All packages from a single repo should have a common naming convention.  This is another indicator that they are from different repositories.

Naturally, the mixing of two different versions/repos of the same package can lead to breakage.

Thank you, I appreciate that :)  Man, I love this place!

---

### Post by il-luzhin on 2007-10-24
I may be in a similar boat
```

luzhin@luzhin-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1            Collection of extra plugins from OpenCompositing for Com
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2            Collection of plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-unofficial           0.0.1+git20070728~jbs0                Collection of UNOFFICIAL fusion plugins for Compiz
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - GNOME window dec
rc  compiz-gtk                                 1:0.3.6-1ubuntu13                     OpenGL window and compositing manager - Gtk window decor
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1          OpenGL window and compositing manager - plugins
ii  compizconfig-settings-manager              0.6.99~git20070926+jbs0               Plugin and configuration tool - Compiz Fusion Project
ii  emerald                                    0.3~git20070717-0ubuntu1              Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1            Settings library for plugins - OpenCompositing Project
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3            Settings library for plugins - OpenCompositing Project
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1              Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1            Compiz configuration system bindings

```

do you have a suggestion?
```

luzhin@luzhin-desktop:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.canonical.com/ubuntu gutsy partner
# deb http://packages.medibuntu.org/ gutsy free non-free

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt feisty main

deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

deb http://archive.canonical.com/ubuntu gutsy partner

# deb http://parker1.co.uk/apt feisty main
# deb-src http://parker1.co.uk/apt feisty main

# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64


```

---

### Post by il-luzhin on 2007-10-26
bump

---

### Post by OliverN on 2007-11-08
I'd hate to see this thread die. I think I might have a similar issue. After upgrading to gutsy, ccsm gives me

```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 24, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

which seems kinda similar to your problem. I don't know. This is my sources.list:

```
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://dk.archive.ubuntu.com/ubuntu/ gutsy main
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-updates main
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://dk.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-backports main universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy-backports main universe multiverse

deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-security main
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy-security main
# deb http://dk.archive.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ gutsy-security multiverse

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt feisty main

deb http://archive.ubuntu.com/ubuntu gutsy-backports restricted

deb http://archive.ubuntu.com/ubuntu gutsy-updates restricted

deb http://archive.ubuntu.com/ubuntu gutsy-security restricted

deb http://archive.ubuntu.com/ubuntu gutsy restricted


# deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-updates universe multiverse

deb http://dk.archive.ubuntu.com/ubuntu/ gutsy-security universe
#AUTOMATIX REPOS END
# deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

I've tried uninstalling and reinstalling everything related to compiz through Synaptic. Compiz is generally working, it's only the manager that wont start.

It seems I get a similar error while trying to open my software sources manager:

```
$ gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

---

### Post by OliverN on 2007-12-10
Well, I started [my own thread]("http://ubuntuforums.org/showthread.php?t=610339") and received a fix of sorts. Perhaps you should try it out.

Cheers.

---

