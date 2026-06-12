---
title: "updating problems"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by grimdaze on 2005-10-17
when i run sudo apt-get update i get this error

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Fetched 20.2kB in 1s (13.8kB/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

why?
also have a similar problem trying to get gdesklets and kubuntu-desktop
it says something about 404 error
what am i missing?

---

### Post by ecobuntu on 2005-10-17
Everyone is having this problem today.  I think the managers of the repositories are having problems right now.  Just be patient and try again later.  Also try to look at other forum posts before posting if it's already been asked!

:)

---

### Post by grimdaze on 2005-10-17
oh ok ......sorry i was in a hurry.........and i didn't notice any similar topics

---

### Post by dbott67 on 2005-10-17
You need to change your sources.list file to what I've posted in this thread:
> The sources.list has worked for others with similar problems, as noted in [this thread]("http://www.ubuntuforums.org/showthread.php?p=411974").

-Dave

---

### Post by grimdaze on 2005-10-17
thanks man works perfect now

---

### Post by dbott67 on 2005-10-17
[QUOTE=grimdaze]thanks man works perfect now[/QUOTE]

You're welcome.

-Dave

---

