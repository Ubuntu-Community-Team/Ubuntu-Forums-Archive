---
title: "upgrading firefox &quot;1.5.0.5&quot; to &quot;1.5.0.6&quot;"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by happyweb on 2006-08-26
hello everyone , 
i m back with another query
i recently updated my ubuntu using its inbuilt update manager
and along with other upadtes it also upgarded firefox from
1.5.0.1 to 1.5.0.5
however since then ,in the firefox "Help" menu, the "Check for Updates.."
option is now permanently unhighlighted and can't use this option to update
firefox , moreover i also downloaded the linux verison of " firefox 1.5.0.6 "
ie. "firefox-1.5.0.6.tar.gz" now can anyone please tell me how to update or install firefox and get to 1.5.0.6

thanks in advance

---

### Post by Crosbie on 2006-08-26
The latest Ubuntu package for Firefox is 1.5.0.5.  Unless you really need to update to .0.6 can i suggest waiting till the official Ubuntu version becomes available? I'd guess it's undergoing testing... see [here](http://www.ubuntuforums.org/showpost.php?p=1345511&postcount=12) and [here](http://www.ubuntuforums.org/showpost.php?p=1387451&postcount=28) for a suggested explanation.  Basically the latest Ubuntu version is fine.

---

### Post by Paul133 on 2006-08-26
How do you install tar's anyway? I keep seeing packages in tar.gz but I can't remember how to install them! And how do you go to the repositories?

---

### Post by Crosbie on 2006-08-26
If you're a newb (like me :) ) then I'd avoid any tar.gz packages.  Use System > Administration > Synaptic Package Manager to check for the tailormade Ubuntu version of any program you desire.  It's probably there.

Within Synaptic you can download programs from the repositories, and add new repositories through the Settings menu.  If you need to add wider repositories (to make some non-free programs available, for example) have a look around these forums or the Ubuntu site, where you'll find instructions.  I believe programs like EasyUbuntu do this too.

---

### Post by Klaidas on 2006-08-26
> **Paul133 said:**
> How do you install tar's anyway? I keep seeing packages in tar.gz but I can't remember how to install them! And how do you go to the repositories?

Tars are usually for compiling.
You must have build-essential installed, then after you untar it, you do > ./configure
make
sudo make install

But there's really no need to install firefox 1.5.0.6 from tars on Ubuntu.

---

### Post by deanjm1963 on 2006-08-26
There was another post somewhere about the exact same thing. It turns out that the version of Firefox in Ubuntu is 1.5.0.6, tho it still says 1.5.0.5. The only fix from .5 to .6 was a problem with windows (as in the MS kind) and video. The Ubuntu developers patched Firefox with the fix before putting it in the repos, if I remember right, there was only a couple of days between .5 and .6 being released from mozilla, and .5 hadn't hit the Ubuntu repos yet so they incorporated the fix.

---

