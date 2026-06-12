---
title: "opera 9 and ubuntu upgrade"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by claudios on 2006-06-13
Hi everyone,
normally I never ask for help because I find everything around but this time I found nothing.
I explain.
After installing opera 9 beta I can't use the - Application - Add/remove anymore, also the ubuntu upgrade doesn't work.
Both says there's a broken package that need to be fixed.
But the requirement to fix  is to delete the package (Opera).
There's anyway I can tell Ubuntu to leave a software alone (no checking)???
Opera is working perfectly!
I installed the software like this:
sudo dpkg -i opera_9.0-20060518.6-shared-qt_en_etch_i386.deb
These are the results:
Selecting previously deselected package opera.
(Reading database ... 79760 files and directories currently installed.)
Unpacking opera (from opera_9.0-20060518.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on xlib6g (>= 3.3.6) | xlibs; however:
  Package xlib6g is not installed.
  Package xlibs is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera

sudo apt-get -f install

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  opera
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 12.6MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


I cannot find the packages missing but the software works perfecly.
Someone can help?

Claudio.

---

### Post by CronoDekar on 2006-06-13
Try installing this, and then reinstalling Opera:

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb)

Not sure if it'll fix your Add/Remove problems, but it'll get Opera going.

---

### Post by claudios on 2006-06-13
Well, as I said Opera is already working perfectly but tonight I'l try and I'll let you know.
Now I am having some doubts about Ubuntu....
I'd like to install a software and have the chance to choose to have it appearing in the list of installed programs or not.
Do you think there's some way to hide to Ubuntu an installed software?
I don't like the fact that Ubuntu want me to de-install Opera just because for him the package is broken or because it doesn't like it :mad: 
Thanks for the reply.

---

### Post by CronoDekar on 2006-06-13
Honestly?  I don't know.  I haven't had this problem, I just know that Opera asks for the xlibs, and I'm just guessing at the solution to your problem.  I do imagine though that if you install xlibs and reinstall Opera, the problems should go away... but again, just guessing.

---

### Post by claudios on 2006-06-14
You are the man,
I've just installed this package, without deinstalling Opera....
everything's working again.
Now I'm facing other kind of smaller problems but the answers are already in the forum :-)
Thank you

---

### Post by xael on 2006-06-14
claudios,

The same thing happened to me the other day, but after installing the xlibs package, the system didn't complained anymore about anything broken & I'm able to install/ remove whatever I want with zero problems.

---

