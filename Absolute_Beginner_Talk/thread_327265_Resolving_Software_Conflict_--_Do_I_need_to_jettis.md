---
title: "Resolving Software Conflict -- Do I need to jettison Ubuntu 6.10?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2006-12-28
I am running Edgy Eft (6.10): When I try to install Gnome Sword 2 Bible Guide I get the following error:

-------------------------------------
Cannot install 'Gnomesword
This application conflicts with other installed software. To install 'gnomesword' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.
--------------------------------------

Questions:
(1) Does 'advanced mod refer to "Synaptic Package Manager'?  (If not what is the 'Advanced Mode')?


(2) Once in Advanced Mode what do I look to remove since the error message gives no specifics?

(Prior to this I did have the KDE bible program (Bible Time 1.6) installed, but it crashed whenever resources were accessed within the program. . . don't know if this has left detritus that needs to be removed)

---

### Post by meng on 2006-12-28
What method of installation are you using?

---

### Post by qamelian on 2006-12-28
If you're doing this through Applications > Add/Remove..., then yes, it is referring to Synaptic Package Manager.

---

### Post by meng on 2006-12-28
Easiest method of installation would seem to be going to terminal and:
sudo aptitude install gnomesword

---

### Post by chaplanger on 2006-12-28
The only method I know of (extreme newbie in Linux here) -- Add/Remove Applications applet from the Applications drop-down menu.

---

### Post by ComplexNumber on 2006-12-28
>  Cannot install 'Package X'
This application conflicts with other installed software. To install 'Package X' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.i got sooooo many of these when i were using ubuntu. the only solution is to not install the package, or wait a few days/weeks until the dependencies have been resolved.

you can fire up the terminal and  try 'sudo apt-get install gnomesword', then enter your password....and hope

---

### Post by chaplanger on 2006-12-28
after running: sudo aptitude install gnomesword
 from the terminal I get the following:
--------------------
The following NEW packages will be installed:
  libgnutls12 sword-comm-mhcc sword-dict-naves sword-text-arasvd 
0 packages upgraded, 5 newly installed, 0 to remove and 36 not upgraded.
Need to get 5719kB of archives. After unpacking 11.6MB will be used.
The following packages have unmet dependencies:
  gnomesword: Depends: libsword5c2a (>= 1.5.8-7) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnomesword [Not Installed]
--------------------
 -- The only answer that is accepted is "y" for yes.  Basically I still do not have the program installed.  Where do I go from here?  I really don't understand what is needed or how to complete the process. . . (BTW is this something I caused by adding other software or is this a edgy eft problem?)

---

### Post by ComplexNumber on 2006-12-28
> **chaplanger said:**
> after running: sudo aptitude install gnomesword
 from the terminal I get the following:
--------------------
The following NEW packages will be installed:
  libgnutls12 sword-comm-mhcc sword-dict-naves sword-text-arasvd 
0 packages upgraded, 5 newly installed, 0 to remove and 36 not upgraded.
Need to get 5719kB of archives. After unpacking 11.6MB will be used.
The following packages have unmet dependencies:
  gnomesword: Depends: libsword5c2a (>= 1.5.8-7) which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gnomesword [Not Installed]
--------------------
Basically I still do not have the program installed.  Where do I go from here -- I really don't understand what is needed or how to complete the process. . .
try uninstalling libsword5c2a then reinstalling it again with gnomesword (i doubt that this will work, but its just clutching at straws). 
otherwise see my first option, above.

---

### Post by chaplanger on 2006-12-28
If I just wait -- how will the dependencies get resolved?  What am I missing here?  Will this be part of a push update from Ubuntu?

---

### Post by ComplexNumber on 2006-12-28
> **chaplanger said:**
> If I just wait -- how will the dependencies get resolved?  What am I missing here?  Will this be part of a push update from Ubuntu?
because the missing dependencies are updated and added to the repositories. for example, package A depends upon Package B(version 1.1), but only Package B(version 1.0) is available in the repositories.

---

### Post by chaplanger on 2006-12-28
RESOLVED!!! :)

Discovered the sister forum for Ubuntu Christain Edition -- went to the following website [http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/about-ubuntu-christian-edition.html)
and downloaded the torrent update to CE -- found the gnomes word files and installed them, then went back to the Applications drop down and Add/Remove and could now install gnome sword!!!

Many Thanks to the community for your assistance -- hope this helps someone with similar problem!

---

