---
title: "Synaptic Package Manager opens but then shuts down immediately"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Kouki on 2006-10-24
Hi, I think this is my first post on this forum as normally the search button helps with most problems I've encountered.  However, I can't find anything on this problem.

Basically, ubuntu was working fine the last time I used it, however, I opened it up today and discovered that whilst everything else works fine, Synaptic package manager has died.  Basically, when I try to open it, it opens, I see it for under a second and then it closes.  Obviously this leaves me with little room for fiddling around in SPM to find out what the problem is.

Anyone got any idea what the problem is?  If there's a solution, I usually like a block of text that I just have to copy and paste into terminal to fix if thats the solution :mrgreen:   I'm still working out the common commands, at present it all looks like a load of gibberish, but I've worked out how to find the gibberish that I need and how to paste it into the terminal.

Just in case it comes in useful, here is my sources.list text:

# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

:confused:  Any pointers would be great \\:D/

---

### Post by bapoumba on 2006-10-24
Even though your sources.list could be improved, that is not the problem. What do you get with **gksudo synaptic** from a terminal ?

edit : see the [documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu") for your sources.list once synaptic problems are fixed up.

---

### Post by gpothier on 2006-10-24
Try to start synaptic from a terminal to see if it prints an error message: open a terminal and type "sudo synaptic"

---

### Post by Kouki on 2006-10-24
Thanks for the advice, I'll try these suggestions and post the results as soon as I get it's latest suprise fixed.  [http://ubuntuforums.org/showthread.php?t=283445](http://ubuntuforums.org/showthread.php?t=283445)

I'm back in windows now as ubuntu won't even start, so I'll have to try your suggestions next time ubuntu works.  Hopefully this won't be too long, but the problem is way beyond my capabilities now ](*,)

---

