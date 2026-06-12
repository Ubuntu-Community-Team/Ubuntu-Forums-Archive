---
title: "Issues with Upgrade from 7.04 to 7.1"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-11-03
When trying to upgrade from 7.04 to 7.1 the Distribution Upgrade tool stops and gives me the errors 

When trying to upgrade from 7.04 to 7.1 I get the following error message when the upgrade tool is downloading the necessary packages (right term?). The error is:


Error During Update:

Failed to fetch [http://download.tuxfamily.org/3v1deb...6/Packages.bz2](http://download.tuxfamily.org/3v1deb...6/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch
[http://download.tuxfamily.org/3v1deb...6/Packages.bz2](http://download.tuxfamily.org/3v1deb...6/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...86/Packages.gz](http://medibuntu.sos-sts.com/repo/di...86/Packages.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...86/Packages.gz](http://medibuntu.sos-sts.com/repo/di...86/Packages.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz](http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz](http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz) 404 Not Found
__________________


It's been so long since I've done anything with installing linux that I've pretty much forgotten the rudimentary things I did learn. Please help.

---

### Post by overdrank on 2007-11-03
> **snwbord2456 said:**
> When trying to upgrade from 7.04 to 7.1 the Distribution Upgrade tool stops and gives me the errors 

When trying to upgrade from 7.04 to 7.1 I get the following error message when the upgrade tool is downloading the necessary packages (right term?). The error is:


Error During Update:

Failed to fetch [http://download.tuxfamily.org/3v1deb...6/Packages.bz2](http://download.tuxfamily.org/3v1deb...6/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch
[http://download.tuxfamily.org/3v1deb...6/Packages.bz2](http://download.tuxfamily.org/3v1deb...6/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...86/Packages.gz](http://medibuntu.sos-sts.com/repo/di...86/Packages.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...86/Packages.gz](http://medibuntu.sos-sts.com/repo/di...86/Packages.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz](http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz](http://medibuntu.sos-sts.com/repo/di...rce/Sources.gz) 404 Not Found
__________________


It's been so long since I've done anything with installing linux that I've pretty much forgotten the rudimentary things I did learn. Please help.

Hi, if you would use this command in the terminal ```
gksudo gedit /etc/apt/sources.list
``` and place # in front of those repos then run the update it should work. Good luck!

---

### Post by snwbord2456 on 2007-11-03
Thanks, things seem to be going along now. What exactly did you do?

---

### Post by overdrank on 2007-11-03
> **snwbord2456 said:**
> Thanks, things seem to be going along now. What exactly did you do?

When you upgrade those repos are different in Gutsy. So you have to remove them upgrade then get the new repos for Gutsy. If that work please remember to mark the thread as solved under the thread tools. Good luck! :popcorn:

---

### Post by snwbord2456 on 2007-11-03
Solved, thanks.

---

