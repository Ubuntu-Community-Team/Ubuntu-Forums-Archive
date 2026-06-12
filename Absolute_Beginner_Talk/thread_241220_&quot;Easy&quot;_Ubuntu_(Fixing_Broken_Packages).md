---
title: "&quot;Easy&quot; Ubuntu (Fixing Broken Packages)"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by pwn3d on 2006-08-22
Hullo.  I'm in the process of getting Ubuntu up and running properly for the first time, but I'm having issues with EasyUbuntu.  Others have posted the exact same problem but so far no one has provided an adequate reply.

I followed the installation commands as per the developer site, and ticked off the various packages and whatnot within EasyUbuntu that I want installed (primarily the nVidia driver).  EasyUbuntu chugs along, doing its thing for several seconds, but then spits up the "fix broken packages" error message.  I know this command is available in the Synaptic Package Manager, but selecting it from the pull-downs doesn't seem to have any effect.  

What should my next move be here, folks?  Are there specific packages I need to select for fixing?  If so, what would they be?


Waiting with baited breath for any answers,
Chris

---

### Post by deadgobby on 2006-08-22
here you go, here is a link to the same problem you have
[http://www.ubuntuforums.org/showthread.php?t=211970](http://www.ubuntuforums.org/showthread.php?t=211970)
[http://www.linuxquestions.org/questions/showthread.php?p=2365149](http://www.linuxquestions.org/questions/showthread.php?p=2365149)

---

### Post by pwn3d on 2006-08-22
Okay, I tried looking up the broken packages in the SPM and nothing is listed.  I selected "fix broken packages" anyway, ran EasyUbuntu again and got the same "broken packages" error again.  Before this appeared, however, I got a new error message stating "Could not download all repository indexes," with the following details:

> [http://packages.freecontrib.org/plf/dists/dapper/main/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/main/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/restricted/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/universe/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/universe/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/multiverse/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/multiverse/binary-i386/Packages.gz:) 404 Not Found


I tried entering the two commands listed in the thread you cited and restarting EasyUbuntu again, and the same two error messages occur.  According to SPM, there are no broken packages.  Any further suggestions?


Thanks so far,
Chris

---

