---
title: "How do I install selective packages from Dapper using Aptitude? (if possible)"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-06
I'm currently using Breezy. How can I install selective packages (like clamav and phpbb) from Dapper using Aptitude without breaking Breezy? Can I still do a 'aptitude upgrade; aptitude dist-upgrade' on Breezy without breaking the few installed Dapper packages?

Thanks!

---

### Post by evilgold on 2006-03-06
I dont understand why you would need to do this? the repositories are the same. If you really cant wait, just upgrade to dapper, its fairly stable now anyways.

---

### Post by Akhran on 2006-03-06
I would want most of my packages to be from breezy, which I presume to be more stable. Only for those packages that requires to be the latest (eg antivirus scanner like clamav) would I want to install from dapper.

[QUOTE=evilgold]I dont understand why you would need to do this? the repositories are the same. If you really cant wait, just upgrade to dapper, its fairly stable now anyways.[/QUOTE]

---

### Post by gord on 2006-03-06
mixing dapper and breezy is generally not a good idea.
maybe the [backports](http://www.ubuntuforums.org/forumdisplay.php?f=47) project is more what you are looking for

---

### Post by evilgold on 2006-03-06
Both versions should be the same no matter what ubutu version you get them for. The repositories are the same, unless your using unoffical ones, in which case, apt will just get the newest verison unless you specify an older one.

---

