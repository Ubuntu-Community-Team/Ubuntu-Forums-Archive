---
title: "permanent error in linux"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by skidkid87 on 2007-03-09
this error keeps on popping up every time I install or uninstall something on linux  (even when updating):


      E: emacs21: subprocess post-installation script returned error exit status 1
      E: cedet-common: dependency problems - leaving unconfigured
      E: eieio: dependency problems - leaving unconfigured
      E: speedbar: dependency problems - leaving unconfigured



this is what happens when I type "sudo apt-get -f install" :



ramy@ramy-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emacs21 (21.4a-6ubuntu2) ...
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
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-load.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet-loaddefs.elc
Wrote /usr/share/emacs21/site-lisp/cedet-common/cedet.elc
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
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-load.elc
Wrote /usr/share/emacs21/site-lisp/speedbar/speedbar-loaddefs.elc
While compiling toplevel forms in file /usr/share/emacs21/site-lisp/speedbar/speedbar.el:
  !! Wrong type argument ((stringp nil))
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




and now I can't seem to find add/remove programs although it was under the Applications menu

I have no idea what's happening so plz help me out here

---

### Post by eljalill on 2007-03-11
Wow, long error message!

Have you tried apt-get without the -f option?
How about synaptics?

---

### Post by katzul on 2007-03-12
I just got that same error... Any luck in fixing it?

---

### Post by tpdasf on 2007-03-14
same problem here..

---

### Post by tpdasf on 2007-03-14
Nevermind...I uninstalled emacs from synaptic and it fixed my problem

---

