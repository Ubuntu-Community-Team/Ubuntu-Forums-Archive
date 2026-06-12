---
title: "Errors with apt-get"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by jcg on 2006-05-16
I am getting errors with apt-get; can anyone help?
 here is a session with the error.
jcg@schubert:~$ sudo apt-get update
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://download.skype.com](http://download.skype.com) stable Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [60.2kB]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release.gpg
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.0kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy Release
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [17.3kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [35.0kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Sources
Fetched 300kB in 2s (141kB/s)
Reading package lists... Done
jcg@schubert:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  moodle
The following packages will be upgraded:
  libmysqlclient12 libmysqlclient14 mysql-common skype
4 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/9709kB of archives.
After unpacking 83.0MB disk space will be freed.
Do you want to continue [Y/n]? yes
WARNING: The following packages cannot be authenticated!
  skype
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 129478 files and directories currently installed.)
Removing moodle ...
dpkg: error processing moodle (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 moodle
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by aysiu on 2006-05-16
Try ```
sudo apt-get -f install
```

---

### Post by jcg on 2006-05-17
[QUOTE=aysiu]Try ```
sudo apt-get -f install
```[/QUOTE]
Thanks. I did here is the error message
Need more suggestions.
Cheers
jcg
jcg@schubert:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  moodle
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 83.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129478 files and directories currently installed.)
Removing moodle ...
dpkg: error processing moodle (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 moodle
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Caligula on 2006-05-17
my problem exactly...
I stuck...

---

### Post by Caligula on 2006-05-17
here's my output:

```
caligula@anarchy:/usr/bin$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emacs21 (21.4a-3ubuntu1) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50autoconf (source)...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50psvn (source)...
Loading 50sawfish (source)...
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-autogen.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-compat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-edebug.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/ezimage.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/fame.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/inversion.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/mode-local.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/pprint.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/sformat.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/working.elc
Done
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs21/site-lisp/dictionaries-common/flyspell.elc
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50autoconf (source)...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50psvn (source)...
Loading 50sawfish (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50autoconf (source)...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50psvn (source)...
Loading 50sawfish (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-co
mpiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm
.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-
ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-
gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-
html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-
image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-
info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-
texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-
w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/spe
edbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed
at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
 eieio depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
Setting up language-selector-common (0.1.20) ...
Compiling /usr/lib/python2.4/site-packages/kuartetlib/ScrollPane.py ...
  File "/usr/lib/python2.4/site-packages/kuartetlib/ScrollPane.py", line 11
    Pane.__init__(self, parent, x, y, size=[0,0], name='', border=0):
                                                                    ^
SyntaxError: invalid syntax

dpkg: error processing language-selector-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of language-selector-qt:
 language-selector-qt depends on language-selector-common (= 0.1.20); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 language-selector-common
 language-selector-qt
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
caligula@anarchy:/usr/bin$

```

What's going on? I just did a format, it's really weird...

---

### Post by Che_GueVaRRista on 2007-07-21
> **Caligula said:**
> my problem exactly...
I stuck...


Hello there Caligula and JCG. I'm a newbie to Ubuntu myself, and I have (or had) a same problem,


[COLOR="RoyalBlue"]But I just found the solution.[/COLOR]


[COLOR="DarkSlateBlue"]
You both have the issue with the program called Moodle. It is a stubborn program, and it won't let you uninstall it (or finish proper installation) unless it is configured. That is what is blocking the terminal and synaptic package manager to get on with the installation and updates of other software.
[/COLOR]


To resolve this, go to synaptic package manager, and search for Moodle. When you have found it, mark "Moodle" for reinstallation. Click Apply. In the beginning it is going to ask you to configure it. Select the offered settings and put in your password, just to get thru with it. You should have it done without much hassle.


Then apply the changes, and hopefully this will finally eliminate the errors and the installation holdup you are going through. 


I did the same, and I could get all the updates, installing it and all the trouble was over.


If you have probs with this, send me a PM.

---

