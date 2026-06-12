---
title: "Fail to fetch fix. 7.04 upgrade"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-04-29
I got some help yesterday on how to fix the following fetch problem. It worked great and I was then able to upgrade without a problem. 7.04 working fine. Hope this helps.

Failed to fetch [http://archive.canonical.com/ubuntu/...6/Packages.bz2](http://archive.canonical.com/ubuntu/...6/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/...6/Packages.bz2](http://archive.canonical.com/ubuntu/...6/Packages.bz2) Sub-process bzip2 returned an error code (2)


Re: Package manager error I think.
You probably need to comment out that repo by placing a # in front of it in /etc/apt/sources.list.

Code:

gksudo gedit /etc/apt/sources.list

Then, run

Code:

sudo aptitude update
sudo aptitude upgrade

__________________
I

---

