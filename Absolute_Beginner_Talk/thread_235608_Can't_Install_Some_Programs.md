---
title: "Can't Install Some Programs"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by groberts1980 on 2006-08-13
I am trying to install vpnc using sudo apt-get install vpnc, but get the below errors. I tried installing emacs21, cedet-common, eieio, and speedbar, but the same errors show up. I get these same errors when I try to install anything through Synaptec as well.

I assume it won't install some programs because emacs21 and the others are needed, and not installed, but I can't seem to install them either.

Can anybody tell me what I can do to get rid of these errors?


```

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
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by jordilin on 2006-08-13
Take a look at system logs at /var/log/messages or syslog to see any clues. Show us your /etc/apt/sources.list as well

---

### Post by kebes on 2006-08-13
It may be that some packages didn't install properly (crash during install?), meaning your packages are in a broken state. Try this:
```

dpkg --audit
```

This may indicate which packages are broken/half-installed. Either way, you can try to fix the packaging with:

```

sudo dpkg --configure -a

```

Afterwards update your lists again:
```

sudo aptitude update

```
(Generally it's better to use "aptitude" instead of plain-old "apt-get", but either will work.)

And then try to do your install again:
```

sudo aptitude install vpnc

```

If that doesn't work, check out the manpages for "aptitude", "apt-get", "dpkg" and related commands... see if they provide other ways to fix a broken dependency system. For instance, you could try removing all the involved packages, clearing your repository list (in "/etc/apt/sources.list"), then doing "sudo aptitude update" and then addint the repositories back into your "sources.list" and doing "sudo aptitude update" again. Hopefully after all this you will have a correct package database and you can install.

Hope that helps.

---

### Post by aysiu on 2006-08-13
Dependency errors usually stem from conflicting repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again.

---

### Post by groberts1980 on 2006-08-13
Running: dpkg --audit

Yields this:
```

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 cedet-common         Collection of Emacs Development Environment Tools - commo
 speedbar             Everything browser, or Dired on steroids
 eieio                Enhanced Implementation of Emacs Interpreted Objects

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 emacs21              The GNU Emacs editor

```

Based on that, I ran: sudo dpkg --configure emacs21

Which gave me this, with errors at the bottom:
```

Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
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
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs21

```

Just running: sudo dpkg --configure -a
Yields this:
```

Setting up emacs21 (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
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
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
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
Errors were encountered while processing:
 emacs21
 cedet-common
 speedbar
 eieio

```

Does any of this help?

---

### Post by kebes on 2006-08-13
Is there any reason that there is so much compiling going on to install such a standard package? Check your /etc/apt/sources.list file and see if somewhere you have a "deb-src" line when you meant to have a standard "deb" line.

---

### Post by groberts1980 on 2006-08-13
These are the only uncommented lines in the sources.list file:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse


I only just installed Dapper yesterday, dual booting a laptop with XP. Is that the reason for all the compiling?

---

### Post by kebes on 2006-08-13
> **groberts1980 said:**
> I only just installed Dapper yesterday, dual booting a laptop with XP. Is that the reason for all the compiling?

That's a very strange sources.list file. That's not what it normally looks like after a fresh install. And yes, that's the problem: when installing emacs it has no choice but to grab the source code and compile it, since you don't have a standard repository defined.

This is a more typical "/etc/apt/sources.list", which is more typical right after a fresh install:

```

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univers multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

I believe "emacs" is in the main repository, but you can uncomment the universe lines if you need to. The important thing is to make sure that you don't just have "deb-src" defined for a particular repository, but that you also have the corresponding "deb" defined.

You can thus edit your sources.list (or just copy the one above), and then do the usual:
```

sudo aptitude update

```

...and then you should be able to install the packages you need.

---

### Post by groberts1980 on 2006-08-13
Sorry, what I posted was just the uncommented lines in the sources.list. Here is the whole thing:

```


deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu/ dapper-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

I did run:
```

sudo aptitude update command

```
with the sources.list file I posted and still get the same errors when trying to install.

Should I try uninstalling programs that are partially configured, then installing them again? See my above post for what happens when I run:
```

dpkg --audit

```

---

### Post by kebes on 2006-08-13
Your sources.list is missing the repository you want. At the top, add this line:

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

Then start back the whole process from the beginning:

```

sudo aptitude update
sudo aptitude remove emacs21
sudo aptitude install emacs21

```

(and then get on to actually installing the program you wanted to)

I'm not sure how that crucial line got cut from your sources.list, but adding it back it should fix everything.

---

### Post by groberts1980 on 2006-08-14
I added the line:
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
To the top of the sources.list file and ran:
sudo aptitude update

Then ran:
sudo aptitude remove emacs21

And got this:
```

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  cedet-common eieio
The following packages have been kept back:
  libwmf0.2-7
The following packages will be REMOVED:
  emacs21
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 6050kB will be freed.
The following packages have unmet dependencies:
  cedet-common: Depends: emacs21 but it is not installable or
                         emacsen which is a virtual package.
  eieio: Depends: emacs21 but it is not installable or
                  emacsen which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
emacs21-nox [21.4a-3ubuntu2 (dapper, now)]

Score is -19

Accept this solution? [Y/n/q/?]

```

Hit Y and got this:
```

The following NEW packages will be automatically installed:
  emacs21-nox
The following packages have been kept back:
  libwmf0.2-7
The following NEW packages will be installed:
  emacs21-nox
The following packages will be REMOVED:
  emacs21
0 packages upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B/1809kB of archives. After unpacking 340kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 76205 files and directories currently installed.)
Removing emacs21 ...
emacs-remove emacs21
remove/eieio: purging byte-compiled files for emacs21
remove/speedbar: purging byte-compiled files for emacs21
emacsen-common: Handling removal of emacsen flavor emacs21
emacsen-common: purging byte-compiled files for emacs21
remove/dictionaries-common: Purging byte-compiled files for flavour emacs21
remove/cedet-common: purging byte-compiled files for emacs21
Selecting previously deselected package emacs21-nox.
(Reading database ... 76195 files and directories currently installed.)
Unpacking emacs21-nox (from .../emacs21-nox_21.4a-3ubuntu2_i386.deb) ...
Setting up emacs21-nox (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars (source)...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Error while loading 50dictionaries-common
Loading 50festival (source)...
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
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21-nox (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not installed.
  Package emacs21-nox which provides emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not installed.
  Package emacs21-nox which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not installed.
  Package emacs21-nox which provides emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not installed.
  Package emacs21-nox which provides emacsen is not configured yet.
 eieio depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21-nox
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up emacs21-nox (21.4a-3ubuntu2) ...
emacs-install emacs21
install/cedet-common: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
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
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Wrote /etc/emacs21/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs21/site-lisp/debian-startup.elc
Done
install/speedbar: Handling install for emacsen flavor emacs21
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 50dictionaries-common (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...
Loading 50festival (source)...
Source file `/usr/share/emacs21/site-lisp/speedbar/dframe.el' newer than byte-compiled file
Wrote /usr/share/emacs21/site-lisp/speedbar/bigclock.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/dframe.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/rpm.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-ant.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-gud.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-html.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-image.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-info.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/sb-rmail.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-texinfo.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/sb-w3.el:
  !! Wrong type argument ((stringp nil))
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Done
emacs-install: /usr/lib/emacsen-common/packages/install/speedbar emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 5.
dpkg: error processing emacs21-nox (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of eieio:
 eieio depends on emacs21 | emacsen; however:
  Package emacs21 is not installed.
  Package emacs21-nox which provides emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not installed.
  Package emacs21-nox which provides emacsen is not configured yet.
dpkg: error processing eieio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cedet-common:
 cedet-common depends on emacs21 | emacsen; however:
  Package emacs21 is not installed.
  Package emacs21-nox which provides emacs21 is not configured yet.
  Package emacsen is not installed.
  Package emacs21 which provides emacsen is not installed.
  Package emacs21-nox which provides emacsen is not configured yet.
dpkg: error processing cedet-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of speedbar:
 speedbar depends on cedet-common; however:
  Package cedet-common is not configured yet.
dpkg: error processing speedbar (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21-nox
 eieio
 cedet-common
 speedbar

```

I was thinking removing and reinstalling might fix the problem, but it won't let me remove emacs21.

I just want to say I appreciate your help with the situation. I literally cannot install anything until this problem is resolved.

---

### Post by kebes on 2006-08-14
Okay... I think we're getting closer. Your sources.list is probably okay now, but you have all kinds of "half installed" packages. That is part of the problem. So you are going to have to do:
```
sudo aptitude remove speedbar --purge-unused
```
for each of these packages:

emacs21-nox
eieio
cedet-common
speedbar

I'm not sure what order to do them in... but you have to get rid of them all. I would try getting rid of one, and see if it gives errors or not. If it does, try another one. Eventually you'll figure out the order that removes them. The "--purge-unused" switch will also remove any non-needed packages as you go along. Once you've managed to remove emacs21, do:

```

sudo dpkg --configure -a
sudo aptitude update

```

Hopefully after all that you'll be able to install your package.

You're quite welcome for all the help. I'm sure you're getting slightly frustrated, but I think we're on the right track.

---

### Post by groberts1980 on 2006-08-14
That seems to have cleared things up. Again, thank you for helping me out. I **was** getting a little frustrated there!

I've been getting a lot of help on the forums here, but most of it has been the "direct commands" type of help that you've given me. While it has solved the problem, I personally don't know **why** it solved the problem. I'm very new to Ubuntu, and the Linux operating system as a whole. What I need to do now is start learning the "why" that is behind the "how." Know what I mean?

Thanks again!

---

### Post by kebes on 2006-08-15
> **groberts1980 said:**
> That seems to have cleared things up. Again, thank you for helping me out. I **was** getting a little frustrated there!

Glad it worked! Now you can get back to having fun with Ubuntu.

> I've been getting a lot of help on the forums here, but most of it has been the "direct commands" type of help that you've given me. While it has solved the problem, I personally don't know **why** it solved the problem. I'm very new to Ubuntu, and the Linux operating system as a whole. What I need to do now is start learning the "why" that is behind the "how." Know what I mean?

Yeah I know exactly what you mean. In the forums we're usually focused on the "fix it now" mentality. We just want to make it work and sometimes forget to contextualize the suggestions. I know I've sometimes blindly followed a suggestion without really understanding it.

What I find helps is whenever there is a suggestion made, I look up a little bit about it. So if someone says "sudo dpkg --configure -a" I go read up about the "dpkg" command and what the "--configure" option really does. On the commandline you can always type:
```

man commandname
```

To get help (the MANual page) for any command. (Note: type 'q' to get out of a man-page... it took me awhile to figure that one out!) This is a great way to figure out what's going on with commands. man-pages can be cryptic, but often if you look at the options available for a command, you'll find that the answer is right there!

Also, I think it's perfectly legitimate to ask, during a thread, "what does that do, exactly?" In fact the best way to learn is during the resolution of problems... but you have to understand what the fix was!

So if you have any questions about what the commands were really doing, feel free to ask.

> Thanks again!

No problem, and have fun!

---

