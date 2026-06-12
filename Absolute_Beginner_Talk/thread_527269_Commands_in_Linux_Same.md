---
title: "Commands in Linux Same?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-16
I just have a quick question.

Are all the commands in Linux the same.  I've like to look at other
Distros to see what feels right for me.  If I learn commands in 
one Distro, will they be the same in another?

Thanks

---

### Post by Bachstelze on 2007-08-16
It depends. The basic commands like cp, mv, rm, cat, ls and so on (a.k.a. the "coreutils") are the same. Also, there are some programs that are de-facto standards and are installed in almost every distribution (wget, nano, links...). However, some things differ, for example the commands used for package management (dpkg for Debian, emerge for Gentoo, pkgtool for Slackware, etc.).

---

### Post by talby on 2007-08-16
For the most part yes, there will be difference with package management tools i.e. ubuntu & debian based ones use "apt-get" to manage .deb packages and rpm-based ones like redhat / fedora and suse use .rpm packages & "yum" to manage them but the basic shell commands and the gui tools are basically the same between distros.

---

### Post by p_quarles on 2007-08-16
Mainly, yes. Since Linux "commands" are essentially applications, though, you'll find that different distros are built around different basic kinds of apps. Debian-based distros (Ubuntu included) use the apt package manager. The others do not. Some distros do not include the gzip compression program by default. Just a couple examples.

---

