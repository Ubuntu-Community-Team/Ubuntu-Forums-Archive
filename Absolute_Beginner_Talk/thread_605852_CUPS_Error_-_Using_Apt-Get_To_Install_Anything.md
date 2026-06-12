---
title: "CUPS Error - Using Apt-Get To Install Anything"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by pimpaulogy on 2007-11-07
About two or three days ago, I powered my laptop on and was notified that there were some updates available.  So, I click to have them installed.  Apparently, they didn't complete properly because since then, when ever I run Synatic, or Apt-get, or Aptitude, I get the same error message at the bottom of the process text:


> sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cupsys (1.3.2-1ubuntu7.1) ...
Reloading AppArmor profiles : done.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cupsys-driver-gutenprint:
 cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5); however:
  Package cupsys is not configured yet.
  Package cups is not installed.
dpkg: error processing cupsys-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cupsys
 cupsys-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)
 

The code above came from what happens when I just try to do an apt-get upgrade

Not sure what to do or try.

---

### Post by dwhitney67 on 2007-11-07
*Package cups is not installed.*

Try installing CUPS.  If you already have it installed, remove it, and then re-install it.

*cupsys-driver-gutenprint depends on cupsys (>= 1.2.5) | cups (>= 1.2.5);*

In English, this means that the GutenPrint depends upon version 1.2.5 (or greater) of either CUPS or CUPSys.

---

### Post by pimpaulogy on 2007-11-07
Should I be fearful of removing CUPS since it also says its going to remove ubuntu-desktop?

I thought I had removed ubuntu-desktop once before and lost the sweet gui interface.  I got it reinstalled but can't remember if my settings were still there or if I had to setup the desktop again.

---

### Post by dwhitney67 on 2007-11-07
abort - abort - abort


Do not remove CUPS.  Try to see if it is possible to upgrade it.  It's been awhile since I used apt-get, but I think the syntax is:

$ sudo apt-get update cups

Also, if your system is running/humming along just fine, skip doing updates unless it is something important.

---

### Post by pimpaulogy on 2007-11-07
Not to worry, I didn't do it.  Like I said, I did it once before which made me take a little more notice before just clicking OK or Yes.

I went through Synaptic and do the whole reinstall (update) thing, but it still fails when it tries to configure it (I guess).  The update command for Apt-get doesn't take arguments (I guess meaning it doesn't single out one app, but looks at the whole system to see if there is anything out of date or broken, I get the same error)

I know, updating is a bad habit of mine.  I just assume all updates are great and will make my system run 10 times faster.

Are there anymore suggestions?  I appreciate the help so far.

---

