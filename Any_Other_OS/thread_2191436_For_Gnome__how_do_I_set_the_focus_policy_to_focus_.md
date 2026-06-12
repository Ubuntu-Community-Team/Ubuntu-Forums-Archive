---
title: "For Gnome:  how do I set the focus policy to focus follows mouse?"
date: 2013-12-02
forum: Any Other OS
---

### Post by bkorb on 2013-12-02
And, yes, I am familiar with several threads on this topic:

  [http://ubuntuforums.org/showthread.php?t=1406729](http://ubuntuforums.org/showthread.php?t=1406729)

the problem being that the "System->Preferences" menu does not have a "Windows" entry and search as I might, there is no "Windows Selection" anywhere I can find.  So, either it is no longer configurable, or it has been relocated to an unlocatable place.  :(  Anybody know?

This is "Gnome 2.28.1" for "CentOS release 6.4 (Final)".  Not strictly "Ubuntu", I guess, but even with "red hat" in the search term, I wind up here.  Better answers.  Thank you in advance!!  Regards, Bruce

---

### Post by Frogs Hair on 2013-12-02
There are no supported versions of Ubuntu running Gnome 2.

***Moved to Other OS/Disro Support ***

---

### Post by buzzingrobot on 2013-12-02
Try this: "gconftool-2 -s /apps/metacity/general/focus_mode -t string sloppy". 

No promises, though. I found it via Google.

Meanwhile... I used to run a CentOS desktop, for a year or two. Finally had to move on when the apps I want just weren't available.  There are some potential desktop goodies here: [http://sourceforge.net/projects/fuduntu-el/](http://sourceforge.net/projects/fuduntu-el/) from the former honcho of the former Fuduntu project.

---

