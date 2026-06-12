---
title: "How to install Java"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by cjpkot on 2005-11-08
Some of the internet sights I view are missing links.  Could someone tell me how to install Java.
Thank You

---

### Post by KLineD on 2005-11-08
Please visit [help.ubuntu.com]("http://help.ubuntu.com/starterguide/C/ch03s02.html")

There you can find detailed instructions to install Java.

---

### Post by Beggar on 2005-11-08
[How to install java]("https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca")

---

### Post by Leif on 2005-11-08
[https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

### Post by NeoRc on 2005-11-09
Or you can simply use the "Synaptic Package Manager", and search "j2re" for j2se runtime and "j2sdk" for j2se sdk

---

### Post by cjpkot on 2005-11-09
I went to update my source code as discribed at this sight. [https://wiki.ubuntu.com/forum/software/JavaAp](https://wiki.ubuntu.com/forum/software/JavaAp)

I did everything but got this error when updating.

carl@69-11-41-40jerome:~$ sudo apt-get update
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://ca.archive.ubuntu](http://ca.archive.ubuntu).
com hoary-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 17.2kB in 2s (6293B/s)
Reading package lists... Done
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

How do I run apt-get update to correct errors.
Thank You

---

### Post by Leif on 2005-11-09
[QUOTE=cjpkot]
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

How do I run apt-get update to correct errors.
Thank You[/QUOTE]

I'm getting this with breezy-updates too. I guess it'll be fixed soon. You can ignore it for the moment, and just go ahead with the java install

---

