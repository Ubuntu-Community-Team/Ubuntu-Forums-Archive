---
title: "How-To broken?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by szadek on 2006-08-02
I've been reading through some of the "How-To" posts and some of the links I've tried are broken.  Take the E17 (Enlightenment) post.  I attempted to install this using the posted instructions, and towards the end of the install this occurred.
> *terminal*
[b]CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /root/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave exml
  - installable apps:     entrance e eclair evfs e_utils
  - installable misc:     engage scrot
  - installable proto:    etk etk_server edje_viewer enhance empower entropy ephoto exhibit extrackt
  - installable modules:  bling calendar cpu deskshow devian emu eveil evolume flame language mail mbar mem moon net rain screenshot slideshow snow taskbar tclock uptime weather wlan
  - skipping:             -

  - script action:        install


BUILD PHASE: 1/3
  - running some basic system checks
  - cvs checkout/update

#############################################################################



BASIC SYSTEM CHECKS:
-----------------------------------------------------------------------------
- cvs-dir .................... ok
- creating script dirs ....... ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... grep: /etc/ld.so.conf*: No such file or directorygrep: /etc/ld.so.conf: No such file or directory
cp: cannot stat `/etc/ld.so.conf': No such file or directory
ok (path has been added to /etc/ld.so.conf)
- setting compile options .... ok
-----------------------------------------------------------------------------

CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout source for 'e17' ...
./easy_e17.sh: line 150: cvs: command not found
./easy_e17.sh: line 150: cvs: command not found
./easy_e17.sh: line 150: cvs: command not found
./easy_e17.sh: line 150: cvs: command not found
./easy_e17.sh: line 150: cvs: command not found
FAILED! Next attempt 6 in 23 seconds
[/b]

This isn't the first time this has occured.  I'm just wondering if anyone is checking the How-To threads to see if they still work as advertised?

Thanks and so far, the promise seems great, but the execution of this OS seems lacking.  I'm working on customizing it, I figure at this pace, it will take a long while at best.

---

### Post by croak77 on 2006-08-02
"./easy_e17.sh: line 150: cvs: command not found"

Do you have cvs installed.

---

