---
title: "monodevelopment installation"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by mistermc on 2008-02-26
I am trying to setup Ubuntu 6 LTS as a web server for .net appliactions.
When trying to run the install command:
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol

I get the error:

Couldn't fimd the package MONODEVELOP.

I am assuming that this is because the package isn't installed.  How do I install?

---

### Post by Crooksey on 2008-02-26
```

$ sudo apt-get update
$ sudo apt-cache search mono | grep devel
```

See if the search displays any results.

---

### Post by mistermc on 2008-02-27
here is what is displayed when I run those commands in the previous message:
michael@ubuntu1:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
michael@ubuntu1:~$ sudo apt-cache search mono | grep devel
libslang2-dev - The S-Lang programming library, development version
libxpm-dev - X11 pixmap library (development headers)
mono-devel - Mono CLI runtime with development tools

---

### Post by igknighted on 2008-02-27
```
monodevelop (0.10-0pre1ubuntu6) [universe]
    C#/Boo/Java/Nemerle/ILasm Development Environment
```

You need to add the universe repository to get monodevelop.  I forget how dapper does this... the entries may be there but commented out, but the easiest way would just be to add the word 'universe' after each line that doesn't start with a #.  Additional mono/.net packages may be in multiverse, so you might want to add that as well.

EDIT: Mono in Dapper is very outdated... with a younger and faster moving technology like that, you might be better served by going with Gutsy to get the latest packages, and then upgrading to the next LTS in April.

---

### Post by mistermc on 2008-02-29
I am new to this.  add the universe repository?

---

